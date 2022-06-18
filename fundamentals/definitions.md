# Definitions

Definitions are things that you have given a name to: constants, and functions. Derw calls constants const. Each definition of is composed of two parts: a type line, specifying the type of the definition, and the body, specifying the value it should have.

## Const

A constant is simply a value that does not change.

```elm
name: string
name =
    "Noah"
```

## Function

A function takes arguments to produce a value.

```elm
sayHi: string -> string
sayHi name =
    if name == "noah" then
        "Hi Noah"
    else
        "I don't know you"
```

## Kernel code

### Const

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
