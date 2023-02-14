# Derw

Derw is a programming language aimed at making complex apps in a simple way. It's built on top of TypeScript and Node, so it's easy to have interop with TypeScript.&#x20;

With Derw, you can write both frontend and backend code. The easiest way to write frontend code is with Derw's [html](https://github.com/derw-lang/html) package, which is built upon a model-view-update structure.

{% hint style="info" %}
Want to stay up to date with Derw? Follow the [blog](https://derw.substack.com/) for regular updates, the [Twitter](https://twitter.com/derwlang) for smaller updates and [star the repo](https://github.com/eeue56/derw) to keep it in your list.
{% endhint %}

### What you'll find in this book

This book will walk you through creating projects, language syntax, working with existing TypeScript and Javascript codebases, and details on how the compiler works.

If you have suggested changes, feel free to open issues or pull requests [here](https://github.com/derw-lang/language-docs/)

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

## What can you use Derw for?

Derw is perfect for interactive web apps,. You can also use it to write command line tooling, and servers.

## Derw's concept

Derw prioritizes practicality above all else. The language is designed to empower developers to get things done in a straightforward and intuitive manner. Derw integrates seamlessly with other programming languages to enhance the development experience. Its syntax is particularly well-suited for those familiar with functional programming.

Derw is a language that is open to new ideas and approaches. If there is something that has not been done in Derw before, the community should work towards implementing it, and if it proves to be a valuable addition, it should be incorporated into the language.

While Derw is beginner-friendly, it is also designed to cater to the needs of experienced developers. It strikes a balance between simplicity and functionality, ensuring that developers of all levels can write efficient, high-quality code with ease.

Writing code that is provably correct allows developers to spend less time fixing bugs in production, leading them to deliver better products. Derw is not the answer to everyone's wishes; there are other languages out there that provide features others want, and that's okay! Derw is happy to sit in this space. You, as a Derw developer, should expect a well tested language that moves at a quick speed, helping you to write better code - and enjoy yourself while doing so.

## What is Derw inspired by?

{% hint style="info" %}
Derw is a general purpose, functional, static, strongly-typed language. It may be both lazy and inferring at a later point.
{% endhint %}

Derw as a language is [inspired by a number of languages](https://derw.substack.com/p/a-love-of-languages?utm\_source=w): Elm, Haskell, Python, Idris, TypeScript and Go.

Syntax-wise, Derw is most similar to Elm and Haskell, in that it is an [ML-family](https://en.wikipedia.org/wiki/ML\_\(programming\_language\)) language. The majority comes from Elm, so you'll see things like `:` being used for type definitions, `let..in` for definitions within a function or const, and type aliases rather than record types. Derw additionally adds `do..return` notation, inspired by both Haskell and Idris.&#x20;

Tooling-wise, Derw is influenced by Go, TypeScript and Elm. The Go idea of having excellent built-in tooling for formatting, testing and benchmarking has inspired Derw to provide as many of these features by default. Packages are based on a similar idea to using a git-based package.json dependency tree, but is stripped back so that there are only the basic fields needed and not extended fields like you might find in JavaScript.

Package-wise, Derw follows the Elm convention of packages always being by a particular name or organization. Names for packages should not be cute, but instead follow the convention of being named based on what they do. html should be called html, for example. One break with Elm is that due to the interop-story of Derw, it is possible to have a package.json listing dependencies that your Derw package may use.&#x20;

In terms of pragmatism, Derw follows Python's idea of being useful rather than pure. Derw strives to be a language that allows you to leverage existing code, e.g TypeScript and JavaScript, in a way that allows you to follow functional standards and design.

## How is Derw developed?

Derw started as a collection of libraries for writing TypeScript in a more functional fashion, called [Hiraeth](https://github.com/eeue56/hiraeth). These libraries were mostly for my own use, but as I used them I realized that I needed a language that wasn't TypeScript to write code in my ideally preferred fashion. The best experience I have had to this point for writing web apps has been with Elm, and having been a contributor to Elm, I figured that I could achieve something similar with some differences.

Derw is currently developed in my spare time, but that doesn't mean progress is slow. In fact since Derw started, there's been over 1000 commits to Derw-related projects and repos. The pace really picked up once Derw reached a point where I could start writing things in it and have them work - i.e, once the compiler was generating code and running without bugs. I'm a big believer in designing tooling and APIs through real-world usage. Derw has been used for several real-world apps now, some quite complicated, which helped nail down the remaining bugs.

Every time a new bug is found, I try to add a test to the comprehensive test suite that ensures that the bug won't be encountered again. This allows me to make big refactors quickly.

To keep track of features and bugs, I use a private Pivotal Tracker instance that allows me to write down my thoughts as they come from my head, and prioritize them on a monthly basis. Each month I write up a summary of all the changes on the [Derw blog](https://derw.substack.com/).&#x20;

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

{% content-ref url="guides/testing.md" %}
[testing.md](guides/testing.md)
{% endcontent-ref %}

