# Definitions

Definitions are things that you have given a name to: constants, and functions. Derw calls constants const. Each definition of is composed of two parts: a type line, specifying the type of the definition, and the body, specifying the value it should have.

## Consts

A constant is simply a value that does not change.

```elm
name: string
name =
    "Noah"
```

## Functions

A function takes arguments to produce a value.

```elm
sayHi: string -> string
sayHi name =
    if name == "noah" then
        "Hi Noah"
    else
        "I don't know you"
```

### Lambdas

Lambdas (or anonoymous functions) are functions without a name. You'd typically want to use them for making small functions that you pass to another function, like `List.map`.

```elm
incrementAges: List number -> List number
incrementAges ages =
    List.map (\age -> age + 1) ages
```

## Kernel code

### Consts

Consts simply become TypeScript consts

```typescript
const name: string = "Noah";
```

### Functions

Functions become TypeScript functions. All functions must have a return value

```typescript
function sayHi(name: string): string {
    if (name === "noah") {
        return "Hi Noah";
    } else {
        return "I don't know you";
    }
}
```

### Lambdas

Lambdas are turned into anonymous functions in TypeScript, with each argument being marked as `any`.

```typescript
function incrementAges(ages: number[]): number[] {
    return List.map(function(age: any) {
        return age + 1;
    }, ages);
}
```
