# Async / await

Async / await is a pattern that can be used for managing asynchronus functions, i.e functions that don't complete each function call in order of calling, but rather based on when the task is finished executing. Working with this pattern in JavaScript typically looks like using Promises and callbacks, and modern JavaScript uses two new keywords to manage this: async, which specifies that a function can use await, and await, which specifies that the function should wait until the function provided is finished executing before moving on.

Derw handles this through the use of `do..return`, blocks which can exist within functions, similarly to `let..in` blocks. The main difference is that `do..return` blocks can have top level function calls (i.e without needing to assign the result to a const or a function). Each function call within a do..return block waits until has finished executing before continuing. This means that the order of definitions matter.

Under the hood, these are compiled to async/await JS blocks.
