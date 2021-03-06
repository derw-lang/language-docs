# Installing packages

Derw's packages are Git based, with the ability to use private packages and specific revisions and branches. When fetching a package, Derw checks to see if there is a Node package.json contained within that repo, and if so, it will also pull the npm packages needed.

If you've just cloned a repo for the first time and want to install packages from the derw-package.json, you can simply do:

```bash
derw install
```

If you want to install a new package, you must provide a name and a version. This will be cloned and added to your derw-package.json.

```bash
derw install --name derw-lang/stdlib --version main
```

If you've installed a package at a particular branch and it has updated, simply run `derw install` again and it will fetch the latest version.

```bash
To install a new package run `derw install --name {package name} --version {version}`
Or run me without args inside a package directory to install all packages in derw-package.json
  --name string:		name of the package e.g derw-lang/stdlib
  --version string:		name of the package e.g main or master
  --quiet :		Keep it short and sweet
  -h, --help :		This help text
```
