Verquire-cli: versioned require
===

Installs Node.js modules for use with [verquire](https://github.com/auth0/verquire).

## Getting started

Installation:

```
npm i -g verquire-cli
```

This creates a global install of `verquire` CLI.

## Creating verquire directory structure

Create a `packages.json` file with the spec of modules and their versions you want to install, e.g.:

```json
{
    "mongodb": ["2.0.33", "2.0.30"],
    "async": ["1.0.0", "0.9.0"]
}
```

Create root directory for module installation:

```
mkdir ~/_verquire
```

Run the tool to install modules from spec:

```
verquire install -s ~/packages.json -e ~/errors.json ~/_verquire
```

Upon successful completion, you can set `VERQUIRE_DIR=~/_verquire` environment variable and use the [verquire](https://github.com/auth0/verquire) module in your Node applications to load versioned Node.js modules, e.g.:

```javascript
require('verquire');
var mongo = require('mongodb@2.0.33');
```

## Update package specs

You can update package specifications by adding the latest versions of Node.js modules available on NPM to it. Assuming your `~/packages.json` as before, just run:

```
verquire update-spec -s ~/packages.json -o ~/new_packages.json
```

The `~/new_packages.json` will contain a specification of the same modules as in `~/packages.json`, but with the latest version of each module from NPM added.

This is also a good way to bootstrap the first revision of the package spec. Create a `~/packages.json` file that lists module names without any version information, e.g.:

```json
{
    "mongodb": [],
    "async": []
}
```

then run `verquire update-spec` on it to populate it with the latest versions of these modules from NPM.

## Issue Reporting

If you have found a bug or if you have a feature request, please report them at this repository issues section. Please do not report security vulnerabilities on the public GitHub issue tracker. The [Responsible Disclosure Program](https://auth0.com/whitehat) details the procedure for disclosing security issues.

## Author

[Auth0](auth0.com)

## License

This project is licensed under the MIT license. See the [LICENSE](LICENSE) file for more info.
