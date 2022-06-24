# Compiling and running your code

Now that you have some Derw code, it's time to turn it into something useful. This can be done through either compiling the code, or through bundling it - which also compiles your code.&#x20;

{% hint style="info" %}
Both bundling and compiling have watching support, through the `--watch` flag.
{% endhint %}

{% hint style="info" %}
The best workflow for Derw currently is to have the generated TypeScript files open for your project, to ensure that the TypeScript part compiles
{% endhint %}

## Compiling

Compiling Derw can be done through the `derw compile` command. It will compile everything in your `src` folder and anything that they depend upon. You can specify if you want to generate TypeScript or JavaScript, but the recommended option is TypeScript.

{% hint style="info" %}
Typical usage of `derw compile` doesn't use any flags
{% endhint %}

```bash
Let's write some Derw code
To get started:
Initialize the current directory via `init`
Or provide entry files via `--files`
Or run me without args inside a package directory
  --files [string...]:		File names to be compiled
  --target ts | js | derw | elm | english:		Target TS, JS, Derw, Elm, or English output
  --output string:		Output directory name
  --verify :		Run typescript compiler on generated files to ensure valid output
  --debug :		Show a parsed object tree
  --only string:		Only show a particular object
  --run :		Should be run via ts-node/node
  --names :		Check for missing names out of scope
  --watch :		Watch the files for changes
  --quiet :		Keep it short and sweet
  -h, --help :		This help text
```

You can then run the compiled code via  `ts-node src/<NameOfYourFile>.ts` or `node src/<NameOfYourFile>.js` if you used js as an target. Note that if you used js as a target, your dependencies may need to be compiled if they relied on an npm package that did not provide JavaScript output.

## Bundling

When you produce JavaScript for a website, you would typically want to bundle all the files into a single file. This is done in Derw through `derw bundle`, which uses [esbuild](https://esbuild.github.io/) underneath. Bundling first compiles the Derw code, then uses esbuild to produce a JavaScript file.

```
To bundle, run `derw build --entry {filename} --output {filename}`
To watch use the --watch flag
To produce the smallest bundle use the --optimize flag
  --entry string:		Entry point file to bundle up
  --output string:		Output file to generate
  --quiet :		Don't print any output
  --watch :		Watch Derw files for changes
  --optimize :		Run generated Javascript through minification
  -h, --help :		This help text
```

You would then want to reference the generated file inside a html file, for example:

```bash
derw bundle --entry src/Main.derw --output bundle.js
```

```markup
<html>
    <body>
        <div id="root"></div>
        <script type="text/javascript" src="bundle.js"></script>
    </body>
</html>
```
