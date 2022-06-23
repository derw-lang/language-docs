# Working on the compiler

Right now the compiler is easiest for me to work on, which means that it's better to either open an issue or reach out to me on Twitter before opening a pull request. That being said: well reasoned pull requests that fit into my plans are totally welcome, across any Derw repo.

This repo contains the compiler, which is split into: parser, tokenizer, type checking, cli and generators.

The flow for compliation looks roughly like:

* Split content into blocks of functions, constants, imports, exports and types.
* Tokenize each block
* Parse each block into an AST
* Check names for collisions and imports
* Check types
* Generate target code

The CLI is mostly responsible for handling all these steps, but the library can be used programatically as it is in the [playground](https://github.com/derw-lang/playground/). Each file in the src/cli folder is responsible for the different abilities of the CLI: installing, formatting, bundling, testing, compiling, templating, etc. These functions all follow the same API to make working on them easier. My rule in designing the CLIs is that they should be obvious on how to use them. There should be a limited number of commands: but I don't want developers to need to install multiple tools to perform standard operations, like formatting or testing. It uses [Baner](https://github.com/eeue56/baner) under the hood for parsing the flags and arguments, so check out the [docs](https://github.com/eeue56/baner/blob/main/docs/src/baner.md) for that if you're unsure.

The generation files are split between Derw, TypeScript, Javascript and Elm. Generally the rule is to avoid code sharing between these as much as possible, as it's easier to read when the code is all in one file and you can clearly see what each AST token generates. That being said, there are some shared files - for example, code for handling indentation. Adding a new code generation target is simplest done by copying the TypeScript generation file - but please reach out to me if you have a new target in mind!

The parser follows a simple rule of one function per expression. There should be only one expression type returned by each parser, and figuring out which to call is done by the main `parseExpression` function. The code here is mostly token based, though in some places it is just done through string manipulation. This is intended to be re-written in Derw in the future, so big refactors aren't necessary at the moment.

Every bug encountered in the parser needs to have a test added for it. There's a combination of tests, some running on library code, some running on short snippets to ensure the parser and generators are consistent. You can find this all in the src/tests folder. To make a new test, just copy one of the existing tests and rename it. It must end with `_test.ts` in order for the test runner to pick it up. You can run the whole suite through `npm run test`, or specifics via `npm run test --file {name of file}`. You can also specify a specific function via the `--function {name of function}` flag, useful for testing just the `testParse` or `testGenerate` of each file. There is also the `--only-fails` flag, useful for just seeing failing tests. Typically snippet tests should test block analysis, parsing, generation, and running the generated TypeScript through tsc. Check out src/tests/simple\_function\_test.ts for an example on how each of those is done. You'll want to also have a [derw-lang/stdlib](https://github.com/derw-lang/stdlib/) folder in the same folder as `derw` to ensure that the stdlib tests can run.
