# Repl and playground

You might want to explore Derw in an interactive fashion, and for that there's two tools that are handy: the repl, and the playground.

## Repl

To access the repl, simply run `derw repl.`&#x20;

In the repl, you can enter definitions for  imports, types, functions and consts. They will not be evaluated until you use `:run` or `:show`. Between each definition, you should enter a blank newline so that it will be parsed. If parsed successfully, the repl will inform you - and if not, it will show you any errors.&#x20;

#### :run&#x20;

run will evaluate functions and constants

```elm
> x: void
> x = globalThis.console.log "hi"
> 
Parsed successfully
> :run
hi
>
```

#### :show&#x20;

show will first evaluate the current repl body, then print the value of the named value provided

```elm
> x: number
> x = 1 + 10
> 
Parsed successfully
> :show x
11
>
```

#### :eval&#x20;

eval can be used to run some Derw code without needing a definition

```elm
> :eval 10 + 10
Parsed successfully
20
```

#### :help&#x20;

And if you forget all the above, you can use help to get a reminder

```elm
> :help
Enter some code, followed by a blank newline.
Run the current namespace via :run
And check the values of code via :show <name>
Or evaluate a constant or function with :eval <function> <args>
```

## Playground

The [playground](https://www.derw-lang.com/playground/) currently lets you write Derw code, and see the outputted code in any of the target languages. Later on error messages will be added, along with the ability to import packages and run code in the browser.

&#x20;
