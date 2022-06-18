# Conditionals

In Derw, there are two main types of conditions: if statements, for simple tests of whether something is true or not, and case statements, for pattern matching a value against the possible values it might have. Typically you'd want to use if statements for small checks, and case statements when you have a wide range of possible values.

Both if statements and case statements must have a final value: all branches must have a value have a value.

## If statements

If statements typically look like the following:

```elm
if condition then 
    someValue
else
    someOtherValue
```

Which can be put to use like this:

```elm
sayHi: string -> string
sayHi name =
    if name == "noah" then
        "Hi Noah!"
    else
        `I don't know you, ${name}`
```

They can also be used inline, like

```elm
if condition then someValue else someOtherValue
```

which might look like:

```elm
viewHi: string -> string
viewHi name =
    div 
        [] 
        [] 
        [ if name == "Noah" then text "Hi Noah" else text "I don't know you" ]
```

Typical ways of getting condition are: a boolean value, returning boolean from a function call, or using comparisons (==, !=, <, <=, >, >=).

## Case statements

Case statements typically look like the following:

```
case value of
    somePotentialValue -> someValueToReturn
```

The most common use case is with union types, as shown in the [Types](types.md#union-types) page.&#x20;

You can also match against literal values of strings and numbers. When using literal values, you must provide a default case, for example:

```elm
sayHi: string -> string
sayHi name =
    case name of
        "noah" -> "Hi, Noah!"
        "jeremey" -> "Hello, Jeremy!"
        default -> "I don't know you"
        
binaryToString: number -> string
binaryToString binary =
    case binary of
        0 -> "0"
        1 -> "1"
        default -> "0"
```

Lists can be pattern matched with destuctures, again with a default case being required. In the example below, the pattern looks for one element in the front of a list and calls it x, while calling the tail xs.

```elm
sum: List number -> number
sum numbers =
    case numbers of
        x :: xs -> x + (sum xs)
        default -> 0
```

Multiple list destructures can be chained, for example:

```elm
type Summary = 
    ValidSummary { pageCount: number, currentPage: number} 
    | InvalidSummary { reason: string }

parseSummary: List number -> Summary
parseSummary xs =
    case xs of 
        x :: y :: [] -> ValidSummary { pageCount: x, currentPage: y }
        x :: [] -> ValidSummary { pageCount: x, currentPage: y }
        default -> InvalidSummary { reason: "Too many values" }
```

It is also possible to match against parts of list. This is non-greedy by default for example:

```elm
parseParens: List string -> string
parseParens xs =
    case xs of
        "(" :: middle :: ")" :: rest -> String.join "" middle
        default -> ""
        
somethingWithAMiddle: string
somethingWithAMiddel =
    parseParens [ "(", "hello", ")" ]
    
testSomethingWithAMiddle: void
testSomethingWithAMiddle =
    Test.equals "hello" somethingWithAMiddle 
    
somethingWithoutAMiddle: string
somethingWithoutAMiddel =
    parseParens [ "(", "hello" ]
    
testSomethingWithoutAMiddle: void
testSomethingWithoutAMiddle =
    Test.equals "" somethingWithoutAMiddle 
```

## Kernel code

If statements are turned into typical Javascript if statements. If the if statement is used within a const definition, then the generated if is turned into a ternary.

```typescript
function sayHi(name: string): string {
    if (name === "noah") {
        return "Hi, Noah!";
    } else {
        return "I don't know you";
    }
}

const isMe: boolean = name === "noah" ? true: false;
```

Case statements are turned into switch statements. The case conditional is put into a const which is called `_res` + the body turned into a number. This is to prevent collisions with nested cases. Cases used within a const are turned into functions

```typescript
function sayHello(name: string): string {
    const _res3373707 = name;
    switch (_res3373707) {
        case "Noah": {
            return "Hi Noah";
        }
        case "James": {
            return "Greetings";
        }
        default: {
            return "I don't know you";
        }
    }
}

const isKnownPerson = (function(): any {
    const _res3373707 = name;
    switch (_res3373707) {
        case "Noah": {
            return true;
        }
        case "James": {
            return true;
        }
        default: {
            return false;
        }
    }
})();
```
