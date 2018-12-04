# Next.js + Transpile `node_modules`


**⚠️ Troubles with Next 7?** Please read the [ongoing discussion](https://github.com/martpie/next-plugin-transpile-modules/issues/1).

Transpile untranspiled modules from your `node_modules`.
Makes it easy to have local libraries and keep a slick, manageable dev experience.

#### Differences with `@weco/next-plugin-transpile-modules`

- it is maintained, `@weco`'s seems dead
- it supports TypeScript

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

With `with-typescript`:

```js
const withTypescript = require('@zeit/next-typescript');
const withTM = require('next-plugin-transpile-modules');

module.exports = withTypescript(
  withTM({
    transpileModules: ['somemodule', 'and-another']
  })
);
```
