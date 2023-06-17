# Repositório para configurar Husky e Eslint

```bash
npm install husky --save-dev
```

---------------------------------------------------------------

```json
// no package.json:

"scripts": {
    "prepare": "husky install",
    "testeHusky": "echo 'teste'"
}
```

```bash
npm run prepare
npx husky add .husky/pre-commit "npm run testeHusky"
```

---------------------------------------------------------------
```bash
git add .
git commit -a -m "Primeiro commit, para teste"
```
---------------------------------------------------------------

```bash
//Config Eslint:

npm install eslint --save-dev
npx eslint --init
npm install lint-staged --save-dev
npm install cross-env --save-dev
npm install eslint-plugin-jest --save-dev
```
---------------------------------------------------------------

```json
//.eslintrc.json

{
    "env": {
        "browser": true,
        "es6": true,
        "jest": true
    },
    "extends": [
        "plugin:react/recommended",
        "airbnb",
        "eslint:recommended"
    ],
    "overrides": [
    ],
    "parserOptions": {
        "ecmaVersion": "latest",
        "sourceType": "module",
        "ecmaFeatures": {
            "jsx": true
        }
    },
    "plugins": [
        "react"
    ],
    "rules": {
        "react/react-in-jsx-scope": "off",
        "react/jsx-filename-extension": [1, {"extensions": [".js", ".jsx"]}],
        "semi": ["error", "always"],
    }
}
```

---------------------------------------------------------------

```json
// no package.json:

"lint-staged": {
    "*.js": [
        "eslint --fix",
        "cross-env CI=true npm run test --bail --findRelatedTests",
        "git add"
    ]
},
"scripts": {
    "prepare": "husky install",
    "lint-staged": "lint-staged"
}
```
---------------------------------------------------------------

```
//.husky/pre-commit:

#!/bin/env sh
. "$(dirname -- "$0")/_/husky.sh"
```

``` bash
npm run lint-staged
```
---------------------------------------------------------------
```bash
git add .
git commit -a -m "Teste final do Eslint"
```
