To Reproduce

```
git clone git@github.com:jamestalmage/eslint-3762-repro.git
cd eslint-3762-repro
npm install
npm test
```

The `npm test` command simply lints `index.js`, which fails as follows:

```
/Users/jamestalmage/WebstormProjects/eslint-3762-repro/index.js
  3:9  error  Properties should be quoted as `default` is a reserved word  quote-props
```

Contents of index.js

```js
var assert = require('assert');

var x = {
  default: 'some value'
};

assert.strictEqual(x.default, 'some value');
```

Rule Config

```js
"eslintConfig": {
  "env": {
    "browser": true,
    "node": true
  },
  "rules": {
    "quote-props": [2, "consistent-as-needed", {"keywords": true}]
  }
}
```
