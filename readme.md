## Yeoman generator for ASTAD Polymer projects


## Features

* A Polymer app scaffold built with [Polymer Starter Kit](https://developers.google.com/web/tools/polymer-starter-kit/)
* Sub-generator to create Polymer elements for your app
* [web-component-tester](https://github.com/Polymer/web-component-tester) support
* scaffold for a nodeJS backend
* API-First design using swagger template


## Installation

Install the generator
`npm install -g git+ssh://git@github.com:sponnet/generator-polymer.git`

Make a new directory and cd into it
`mkdir -p my-project && cd $_`

Scaffold a new Polymer project:
`yo astad`

## Generators

Available generators:

- [astad (aka astad)](#app)
- [polymer:element](#element-alias-el)
- [polymer:seed](#seed)
- [polymer:gh](#gh)

**Note: Generators are to be run from the root of your app**

### App
Sets up a new Polymer app, generating all the boilerplate you need to get started.

Example:
```bash
yo astad
```

### Element (alias: El)
Generates a polymer element in `app/elements` and optionally appends an import to `app/elements/elements.html`.

Example:
```bash
yo polymer:element my-element

# or use the alias

yo polymer:el my-element
```

**Note: You must pass in an element name, and the name must contain a dash "-"**

One can also include element dependencies to be imported. For instance, if you're creating a `fancy-menu` element which needs to import `paper-button` and `paper-checkbox` as dependencies, you can generate the file like so:

```bash
yo polymer:el fancy-menu paper-button paper-checkbox
```

#### Options

```
--docs, include iron-component-page docs with your element and demo.html
--path, override default directory structure, ex: --path foo/bar will put your element in app/elements/foo/bar
```

### Seed
Generates a reusable polymer element based on the [seed-element workflow](https://github.com/polymerelements/seed-element). **This should only be used if you're creating a standalone element repo that you intend to share with others via bower.** If you're just building a Polymer app, stick to the [Element](#element-alias-el) generator.

To preview your new element you'll want to use the [polyserve](https://github.com/PolymerLabs/polyserve) tool.

Example:
```bash
mkdir -p my-foo && cd $_
yo polymer:seed my-foo
polyserve
```

### Gh
Generates a Github pages branch for your [seed-element](#seed).

If your documentation or demo pages have dependencies declared as devDependencies in `bower.json`, they will be included in your GitHub pages branch.

Example:
```bash
cd my-foo
yo polymer:gh
```

If, for some reason, you don't want the devDependencies, use the `--nodevdeps` option.

## Testing

The project generated by `yo polymer` contains support for [web-component-tester](https://github.com/Polymer/web-component-tester). The following commands are included:

Run local tests (in terminal):
```bash
gulp test:local
```

Run remote tests with [SauceLabs](https://saucelabs.com/):
```bash
gulp test:remote
```

See the [web-component-tester readme](https://github.com/Polymer/web-component-tester#configuration) for configuration options.

## Gotchas

### The `elements.html` file

The `app` generator will produce an `elements.html` file where you can place your imports. This file will be [vulcanized](https://www.polymer-project.org/articles/concatenating-web-components.html) when you run the default `gulp` task. **You'll want to make sure that elements.html is the only import in your index.html file, otherwise there's a good chance you'll accidentally load Polymer twice and break the app**.


## License

[BSD license](http://opensource.org/licenses/bsd-license.php)
