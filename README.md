# purescript-webpack-example

The NetSuite connector project you know and love, now free of side-effects thanks to GPT-3 and 
PureScript.
![alt text](image "https://ca.slack-edge.com/T3RBGCW1F-U031M1LR6CW-3ccb8971f4c4-512" "image Title")

## Installation

```bash
bower install
npm install
```

## Running

### Using locally installed binaries

On most system this should be enough, because npm should take care of extra
depedencies, including `purescript` and `purescript-psa`.
Note, that this will use the compiler from `node_modules/.bin/`, not
the one that might have installed globally or the one that may be present
in your `$PATH`. This will fail on systems like Nix, where you'll need to use
globally installed binaries (patched version of `psc`, while `npm` will supply
unpatched version).

```
npm run webpack
npm start
```

To test this in the browser with the webpack-dev-server.

```bash
bower install

npm install

# http://localhost:4008/
npm run webpack:server
```

### Using globally installed binaries

`npm install` should have installed extra binary dependencies required to run
this example to `node_modules/.bin`. However, if you want to use the `psc`
compiler that you have installed globally (i.e., the one in `$PATH`), you can
just call webpack directly:

```
webpack
```

As always, you can use `webpack --watch` option to enable automatic recompilation
on file changes.

However, if you want to use globally installed binaries, this means that you'll
have to take care of all binary dependencies yourself. Right now, this includes
having in your `$PATH`:

* `psc` that comes from `purescript` (`haskellPackages.purescript` on Nix)
* `psa` that comes from `purescript-psa` (on Nix, you'll have to install it
yourself via `node2nix -i node-packages.json` and `nix-env -f default.nix -iA
purescript.psa`; node-packages.json is a file you create yourself containing
`[ "purescript-psa" ]`). You can remove the dependency on `psa` by changing `psc: 'psa'`
to `psc: 'psc'` inside `webpack.config.js`. `psa` just provides clearer compilation
messages compared to `psc`
* `webpack` (on Nix, `nodePackages.webpack`)
* `node` that comes from `nodejs`

## Additional examples

 - [Fast rebuilds](https://github.com/ethul/purescript-webpack-example/tree/fast-rebuilds)
 - [Psc package](https://github.com/ethul/purescript-webpack-example/tree/psc-package)
 - [Source maps](https://github.com/ethul/purescript-webpack-example/tree/source-maps)
 - [Spago](https://github.com/ethul/purescript-webpack-example/tree/spago)
