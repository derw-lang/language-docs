---
description: How to test your Derw code
---

# Testing

Derw comes with a built-in test runner via `derw test`. The runner is based on [bach](https://github.com/eeue56/bach), a test runner written in TypeScript.

```bash
To run tests, run `derw test` from the package directory
To watch use the --watch flag
  --watch :		Watch Derw files for changes
  --function string:		A particular function name to run
  --file string:		A particular file name to run
  --only-fails :		Only log failing tests
  -h, --help :		This help text
```

## Writing a test

### Naming your file

Your file must have the extension `_test.derw` to be picked up by the test runner.

### Importing the testing functions

Testing functions are provided by the stdlib, which you can install via:

```bash
derw install --name derw-lang/stdlib --version main
```

These can then be imported like&#x20;

```elm
import "./Test" exposing ( equals, notEquals )
```

### Writing your test

A test function should be called `testNameOfTest`, and have the type `a -> void`. Test functions are automatically exported by the compiler.

```elm
testEmptySplit: a -> void
testEmptySplit =
    split "," ""
        |> equals [ "" ]

testSplit: a -> void
testSplit =
    split "," "a,b,c"
        |> equals [
        "a",
        "b",
        "c"
    ]
```

## In-browser tests

When working with html, you may find yourself needing to test a repeated set of actions in the browser - and ensuring the correct data shows up. This can be done via [html-test](https://github.com/derw-lang/html-test) package. It provides both a html element you can embed for results, and a console output. It is currently a work in progress, but if you're curious you can try it out.

![console output](../.gitbook/assets/test\_runner\_console\_success.gif)

![web output](../.gitbook/assets/test\_runner\_web\_success.gif)
