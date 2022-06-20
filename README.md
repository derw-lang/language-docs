# Derw

Derw is a programming language aimed at making complex apps in a simple way. It's built on top of TypeScript and Node, so it's easy to have interop with TypeScript.&#x20;

With Derw, you can write both frontend and backend code. The easiest way to write frontend code is with Derw's [html](https://github.com/derw-lang/html) package, which is built upon a model-view-update structure.

### What you'll find in this book

This book will walk you through creating projects, language syntax, working with existing TypeScript and Javascript codebases, and details on how the compiler works.

## What does Derw look like?

```elm
sayHi: string -> string
sayHi name =
    `Hello, ${name}`
    
helloWorld: string
helloWorld =
    sayHi "world"
```

You can also check out the [examples](https://github.com/derw-lang/examples) repo for more fleshed out examples.

## Derw's concept

Derw, above all, should be considered pragmatic. Derw developers should be able to get things done in a reasonable manner, with an ideally obvious way to do it. Derw works with other languages to enrich the developer experience, while having a favourable syntax for those used to functional programming. If something has not been done in Derw before, then it should be, and if it's good, then it should be adopted into the language. Beginner friendliness is important, but not at the expense of experienced developers. Writing code that is provably correct allows developers to spend less time fixing bugs in production, leading them to deliver better products. Derw is not the answer to everyone's wishes; there are other languages out there that provide features others want, and that's okay! Derw is happy to sit in this space. You, as a Derw developer, should expect a well tested language that moves at a quick speed, helping you to write better code - and enjoy yourself while doing so.

## What is Derw inspired by?

{% hint style="info" %}
Derw is a general purpose, functional, static, strongly-typed language. It may be both lazy and inferring at a later point.
{% endhint %}

Derw as a language is [inspired by a number of languages](https://derw.substack.com/p/a-love-of-languages?utm\_source=w): Elm, Haskell, Python, Idris, TypeScript and Go.

Syntax-wise, Derw is most similar to Elm and Haskell, in that it is an [ML-family](https://en.wikipedia.org/wiki/ML\_\(programming\_language\)) language. The majority comes from Elm, so you'll see things like `:` being used for type definitions, `let..in` for definitions within a function or const, and type aliases rather than record types. Derw additionally adds `do..return` notation, inspired by both Haskell and Idris.&#x20;

Tooling-wise, Derw is influenced by Go, TypeScript and Elm. The Go idea of having excellent built-in tooling for formatting, testing and benchmarking has inspired Derw to provide as many of these features by default. Packages are based on a similar idea to using a git-based package.json dependency tree, but is stripped back so that there are only the basic fields needed and not extended fields like you might find in JavaScript.

Package-wise, Derw follows the Elm convention of packages always being by a particular name or organization. Names for packages should not be cute, but instead follow the convention of being named based on what they do. html should be called html, for example. One break with Elm is that due to the interop-story of Derw, it is possible to have a package.json listing dependencies that your Derw package may use.&#x20;

In terms of pragmatism, Derw follows Python's idea of being useful rather than pure. Derw strives to be a language that allows you to leverage existing code, e.g TypeScript and JavaScript, in a way that allows you to follow functional standards and design.

## Getting Started

{% content-ref url="guides/creating-your-first-project.md" %}
[creating-your-first-project.md](guides/creating-your-first-project.md)
{% endcontent-ref %}

{% content-ref url="guides/installing-packages.md" %}
[installing-packages.md](guides/installing-packages.md)
{% endcontent-ref %}

{% content-ref url="guides/compiling-and-running-your-code.md" %}
[compiling-and-running-your-code.md](guides/compiling-and-running-your-code.md)
{% endcontent-ref %}

{% content-ref url="guides/formatting.md" %}
[formatting.md](guides/formatting.md)
{% endcontent-ref %}

{% content-ref url="guides/repl-and-playground.md" %}
[repl-and-playground.md](guides/repl-and-playground.md)
{% endcontent-ref %}

