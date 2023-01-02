> Moved to https://github.com/knicola/node-toolkit/tree/master/tools/dev-config

# @knicola/dev-config

## Install
```sh
npm i -D @knicola/dev-config typescript eslint
```

## Setup

.eslintrc.js
```js
require('@knicola/dev-config/eslint.patch')

module.exports = {
    extends: ['./node_modules/@knicola/dev-config/eslint.base'],
    parserOptions: { tsconfigRootDir: __dirname }
}
```

tsconfig.json
```json
{
  "extends": "@knicola/dev-config/tsconfig.base",
  "compilerOptions": {
    "types": [ "node", "jest" ],
  },
  "include": [ "**/*.ts", "**/*.js" ]
}
```

tsconfig.build.json
```json
{
  "extends": "@knicola/dev-config/tsconfig.base",
  "compilerOptions": {
    "removeComments": true,
    "noUnusedLocals": true,
    "outDir": "lib/",
  },
  "include": [ "src/**/*.ts" ]
}
```

package.json
```jsonc
{
  // ...
  "scripts": {
    "lint": "eslint src/ --ext .js,.jsx,.ts,.tsx",
    "build": "tsc -p ./tsconfig.build.json",
  }
}
```
