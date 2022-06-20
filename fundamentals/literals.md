# Literals

## Strings

Regular strings can be denoted through double quotation marks. String interpolation can be done through backticks.

```typescript
"hello world"
`hello ${name}`
```

## Numbers

```elm
10
-10
```

## Booleans

```typescript
true
false
```

## Null

```typescript
null
```

## Lists

```typescript
[ 1, 2, 3, 4 ]
```

## List ranges

```elm
[ 1..10 ] -- produces [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 ]
[ n..m ]
```

## Objects

```typescript
{ name: "Noah", age: 29 }
```

## Spread operator

In order to update an existing object, you can use the `...` spread operator. This will create a new version of the object, which you can then modify fields on. For example:

```elm
type alias Person = {
    age: number,
    name: string
}

person: Person
person = { age: 27, name: "Noah" }

olderPerson: Person
olderPerson = { ...person, age: 79 } -- equal to { age: 79, name: "Noah" }
```
