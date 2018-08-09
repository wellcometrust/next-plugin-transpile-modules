# Next.js + Transpile `node_module`

Transpile untranspiled modules from your `node_modules`.
Makes it easy to have local libraries and keep a slick, manageable dev experience.

⚠️ The main difference with `@weco/next-plugin-transpile-modules` is this one support Next's `with-typescript` plugin: you can transpile TypeScript files.

## Installation

```
npm install --save next-plugin-transpile-modules
```

or

```
yarn add next-plugin-transpile-modules
```

## Usage

```js
// next.config.js
const withTM = require('next-plugin-transpile-modules');

module.exports = withTM({
  transpileModules: ['somemodule', 'oranother']
});
```
