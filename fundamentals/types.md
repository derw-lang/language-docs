# Types

There are two main ways to declare a new type in Derw: type aliases, such as those representing a JSON object, and union types, composed of multiple constructors.

Additionally, both type aliases and union types may take a type as an argument. You might want to use this to represent a generic wrapper, such as a `Maybe`.

Derw's types are typically written in caps case, whereas generic arguments are lowercase. Builtin types, such as those that have direct overlap with TypeScript, are often lowercase.

{% hint style="info" %}
There are some builtin types: string, number, boolean, void, null, any, and List&#x20;
{% endhint %}

## Type aliases

Type aliases are what you'd use to represent your typical data objects. A typical usage is for models.

```elm
type alias Model = {
    age: number

}

initialModel: Model
initialModel =
    { age: 29 }
    
myAge: number
myAge =
    initialModel.age
```



In order to pass a type argument, simply follow the name of the type alias with the type argument.

```elm
type alias Person pet = {
    name: string,
    age: number,
    pet: pet
}

type Dog = {
    tailWags: number
}

type Cat = {
    lives: number
}

me: Person Cat
me = 
    {
        name: "Noah",
        age: 29,
        pet: { lives: 9 }
    }
    
myCatsLives: number
myCatsLives =
    me.pet.lives

you: Person Dog
you = 
    {
        name: "Charlie",
        age: 22,
        pet: { tailWags: 9001 }
    }
    
yourDogsTailWags: number
yourDogsTailWags =
    you.pet.tailWags
```

## Union types&#x20;

Union types are useful for when you want to say _this data has multiple shapes._

Imagine you have multiple modes for a page, and you want to do different things based on the current page. You could use a string, as in the example below.

```elm
viewCurrentPage: string -> HtmlNode msg
viewCurrentPage currentPage =
    case currentPage of
        "home" ->
            div [] [] [ text "Home" ]
    
        "login" ->
            div [] [] [ text "login" ]
        
        default ->
            div [] [] [ text "This should be impossible" ]
```

Using a string requires a default case for when no other strings match, leading you to have impossible states represented in code. Instead, you can use a union type to represent the only possible states, as shown below. Each one of the possible states is known as a tag.

```elm
type PageMode = Home | Login

viewCurrentPage: PageMode -> HtmlNode msg
viewCurrentPage currentPage =
    case currentPage of
        Home ->
            div [] [] [ text "Home" ]
    
        Login ->
            div [] [] [ text "login" ]
```

A particularly useful case for union types is when you want to have an optional data type. You'd represent the contained value as either being there or not. Lots of languages have this concept: optional, maybe, either, result. In Derw's stdlib, Maybe is provided and implemented as the following:

```elm
type Maybe value = Just { value: value } | Nothing

something: Maybe string
something =
    Just { value: "Hello" }
    
nothing: Maybe string
nothing =
    Nothing
    
greeting: Maybe string -> string
greeting maybeGreetingText =
    case maybeGreetingText of
        Just { value } -> value
        
        Nothing -> "No greeting for you"
```

## Kernel code

In the generated TypeScript, union types are represented as TypeScript union types, with a type for each tag. Type aliases are simply a new type. For both union types and type aliases, constructor functions are generated. When generating JavaScript, only the constructor functions are generated.

### Union types

```elm
type Maybe a = Just { value: a } | Nothing
```

compiles into

```typescript
type Just<a> = {
    kind: "Just";
    value: a;
};

function Just<a>(args: { value: a }): Just<a> {
    return {
        kind: "Just",
        ...args,
    };
}

type Nothing = {
    kind: "Nothing";
};

function Nothing(args: {}): Nothing {
    return {
        kind: "Nothing",
        ...args,
    };
}

type Maybe<a> = Just<a> | Nothing;
```

### Type aliases

```elm
type alias Model = { age: number }
```

compiles into

```typescript
type Model = {
    name: string
}

function Model(args: { name: string }): Model {
    return {
        ...args,
    };
}
```
