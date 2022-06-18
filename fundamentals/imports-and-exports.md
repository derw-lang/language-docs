# Imports and exports

When you're working with multiple files, whether they're your own or from a package, you will want to import and export definitions. You'll also want to work with TypeScript or Javascript code, and Derw provides a way to work with that.

## Imports

All imports can either have an alias you provide, or a list of exposed functions which are imported into the current scope. If no alias is provided, the file is imported with the name of the file as the alias. You can export types, functions and consts from other files if they have been exposed. If the an imported type has the same name as the module, then you can refer to the type by its name and also use it for module lookups.

If you want to import from another Derw file, this is the syntax:

```elm
import "./FileName" as FileName
import "./OtherFileName" exposing (sayHi)
import "./FinalFileName"

calulateSomething: string -> string
calculateSomething name =
    FileName.something name

sayHiToSomeone: string -> string
sayHiToSomeone name =
    sayHi name
    
calculateTheFinal: number -> number
calculateTheFinal num =
    FinalFileName.final num
```

If you're working with the stdlib and the html package, then you'd typically have these two imports:

```elm
import "../derw-packages/derw-lang/html/src/Html" as Html exposing ( HtmlNode, RunningProgram, div, text, program, attribute, class_ )
import "../derw-packages/derw-lang/stdlib/src/Maybe" as Maybe exposing ( Maybe, Just, Nothing )
```

When importing from TypeScript or JavaScript local files, the syntax is the same as above. There is no need to include a file extension.

But if you're importing from a global module, for example those provided by node or installed via npm, you can use the syntax:

```elm
import fs
```

## Exports

Exports are done through the exposing keyword. You can have multiple exposing statements, but they must be at the top of the file. You can also expose multiple things in one statement

```elm
exposing (sayHi, sayBye)

sayHi: string -> string
sayHi name =
    "Hi " + name + "!"

sayBye: string -> string
sayBye name =
    "Bye " + name + "!"
```

## Kernel code

### Imports

imports map directly to standard TypeScript imports:

```typescript
import * as fs from "fs";
import * as FileName from "./FileName";
import { sayHi } from "./OtherFileName";
import * as FinalFileName from "./FinalFileName";
import * as Maybe from "./Maybe";
import { Just, Nothing } from "./Maybe";
```

Note that if a type is exposed with the same name as the imported filename, then the generated code will refer to it as `FileName.FileName`.

### Exports

Exports are also standard named exports. There is no default export

```typescript
export { sayHi };
export { sayBye };
```
