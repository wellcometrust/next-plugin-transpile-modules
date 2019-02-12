# Next.js + Transpile `node_modules`

Transpile untranspiled modules from `node_modules`.
Makes it easy to have local libraries and keep a slick, manageable dev experience.

## Compatibility table

| Next.js version | Plugin version |
|-----------------|----------------|
| Next.js 8       | 2.x            |
| Next.js 6 / 7   | 1.x            |

## Installation

```
npm install --save next-plugin-transpile-modules
```

or

```
yarn add next-plugin-transpile-modules
```

## Usage

Classic:

```js
// next.config.js
const withTM = require('next-plugin-transpile-modules');

module.exports = withTM({
  transpileModules: ['somemodule', 'and-another']
});
```

**note:** please declare `withTM` as your last plugin (the "most nested" one).

With `next-typescript`:

```js
const withTypescript = require('@zeit/next-typescript');
const withTM = require('next-plugin-transpile-modules');

module.exports = withTypescript(
  withTM({
    transpileModules: ['somemodule', 'and-another']
  })
);
```

## FAQ

### What is the difference with `@weco/next-plugin-transpile-modules`?

- it is maintained, `@weco`'s seems dead
- it supports TypeScript

### I have trouble making it work with Next.js 7

Next.js 7 introduced Webpack 4 and Babel 7, [which changed a couple of things](https://github.com/zeit/next.js/issues/5393#issuecomment-458517433), especially for TypeScript and Flow plugins.

If you have a transpilation error when loading a page, check that your `.babelrc`/`babel.config.js` is up to date and valid, [you may have forgotten a preset](https://github.com/martpie/next-plugin-transpile-modules/issues/1#issuecomment-427749256) there.

### I have trouble with Yarn and hot reloading

If you add a local library (let's say with `yarn add ../some-shared-module`), Yarn will copy those files by default, instead of symlinking them. So your changes to the initial folder won't be copied to your Next.js `node_modules` directory.

You can go back to `npm`, or use Yarn workspaces. See [an example](https://github.com/zeit/next.js/tree/canary/examples/with-yarn-workspaces) in the official Next.js repo.

### I have trouble making it work with Lerna

Lerna's purpose is to publish different packages from a monorepo, **it does not help for and do not intend to help local development with local modules**.

This is not coming from me, but [from Lerna's maintainer](https://github.com/lerna/lerna/issues/1243#issuecomment-401396850).

So you are probably [using it wrong](https://github.com/martpie/next-plugin-transpile-modules/issues/5#issuecomment-441501107), and I advice you to use `npm` or Yarn workspaces instead.
