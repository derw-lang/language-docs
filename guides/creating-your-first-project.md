# Creating your first project

## Installing Derw

First we need to install Derw. It's recommended that you use the latest stable version of Node, though most supported versions should work. You need ts-node to run the test runner, so it's recommended to install that too.

```
npm install -g ts-node derw
```

## Creating a project

Starting a project is as simple as making a directory, then initializing Derw inside it.&#x20;

```
derw init
```

```bash
Initialize a directory as a Derw project.
  --dir string:		name of a directory to use as package name e.g stdlib. 
                        Defaults to current directory's name
  -h, --help :		This help text
```

### Using templates to get started

Derw comes with some templates to get you started. Right now there is only one template: for creating a web app using Derw's html library.&#x20;

To create a web template, run

```bash
derw template --template web --path src/Main.derw
```

```bash
Generate a Derw file from a template.
Also installs required packages.
  --path string:		path of Derw file to create
  --template web:		Template to use
  -h, --help :		        This help text
```

## Installing editor and CLI utils

Right now the best supported editor is VSCode, with three extensions that can be used in combination to get some nice features

### Install vscode-language-server

The language server supports things like inline error messages.

```
git clone https://github.com/derw-lang/derw-language-server
cp -r derw-language-server ~/.vscode/extensions/derw-language-server-0.0.1
```

### Install Derw syntax

Derw syntax highlighting it provided in a separate extension

```
git clone https://github.com/derw-lang/derw-syntax
cp -r derw-syntax ~/.vscode/extensions/derw-syntax-0.0.1
```

### Install auto-formatter

The auto-formatter runs on-save for files with the .derw extension

```
git clone https://github.com/derw-lang/derw-formatter-vscode
cp -r derw-formatter-vscode ~/.vscode/extensions/derw-formatter-vscode-0.0.1
```

### Install Bash completions

If you use Bash, then you probably want some auto completion.

* Clone this [repo](https://github.com/derw-lang/derw-bash-completion)
* Source the `_derw_completions.sh` files in your `~/.bashrc` or `~/.bash_profile`, using `source`
* Restart bash or open a new terminal session

If you're using Linux, you probably want `.bashrc`. If you're using OS X, you probably want `.bash_profile`.

Example .bashrc or .bash\_profile file:

```bash
for f in ~/dev/derw-bash-completion/_*; do source $f; done
```

#### Oh my Zsh

Use `bashcompinit`.

```bash
autoload bashcompinit
bashcompinit
for f in ~/dev/derw-bash-completion/_*; do source $f; done
```
