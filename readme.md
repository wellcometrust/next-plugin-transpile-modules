# Next.js + Transpile `node_module`

Transpile untranspiled modules from your `node_modules`.
Makes it easy to have local libraries and keep a slick, manageable dev experience.

## Installation

```
npm install --save @weco/next-plugin-transpile-modules
```

or

```
yarn add @weco/next-plugin-transpile-modules
```

## Usage

```js
// next.config.js
const withTM = require('@weco/next-plugin-transpile-modules')
module.exports = withTM({
  transpileModules: ['@weco']
})
```

