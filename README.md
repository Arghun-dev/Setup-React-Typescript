# Easy start of a Typescript/React project (w/ Yarn, ESlint and Prettier)

`https://dev.to/viniciusmdias/easy-start-of-a-typescript-react-project-w-eslint-and-prettier-55d4`

## Create project

```js
$. yarn create react-app *your-application-name* --template=typescript
```


## ESlint

. Add ESlint to the project on the development mode:
```js
$. yarn add eslint -D
```

. Start a new eslint file:
```js
$. yarn eslint --init
```

. Choose these answers for the above command:

1. To check syntax, find problems, and enforce code style
2. JavaScript modules (import/export)
3. React
4. Yes
5. Browser
6. Use a popular style guide
7. Airbnb
8. JSON
9. No


. Install with Yarn the list of required dependencies that appear after denying intall with npm in the last choice of above command (Remove eslint and additional versions of react hooks). The command should look something like this:

```js
$. yarn add eslint-plugin-react@^7.20.0 @typescript-eslint/eslint-plugin@latest eslint-config-airbnb@latest eslint@^7.2.0 eslint-plugin-import@^2.21.2 eslint-plugin-jsx-a11y@^6.3.0 eslint-plugin-react-hooks@^4 @typescript-eslint/parser@latest -D
```

be careful the dependencies can change.

. Create a file `.eslintignore` in the root of the project.

`.eslintignore`:

```js
**/*.js
node_modules
build
```

. Add the following library in the development mode, to import typescript by default:

```js
yarn add eslint-import-resolver-typescript -D 
```

. Add some configurations in file `eslintrc.json`

`eslintrc.json`:

```js
{
  ...
  "extends": [
    ...
    "plugin:@typescript-eslint/recommended"
  ],
  ...
  "plugins": [
    ...
    "react-hooks"
  ],
  "rules": {
        "react-hooks/rules-of-hooks": "error",
        "react-hooks/exhaustive-deps": "warn",
        "react/jsx-filename-extension": [
          1,
          {
            "extensions": [
              ".tsx"
            ]
          }
        ],
        "import/prefer-default-export": "off",
        "import/extensions": [
          "error",
          "ignorePackages",
          {
            "ts": "never",
            "tsx": "never"
          }
        ]
      },
    "settings": {
        "import/resolver": {
            "typescript": {}
        }
    }
}
```

## Prettier

Add Prettier to the project on the development mode:

```js
yarn add prettier eslint-config-prettier eslint-plugin-prettier -D
```

Integrate the prettier with eslint by adding a few more settings to the file

`eslintrc.json`

```js
{
  ...
  "extends": [
    ...
    "plugin:prettier/recommended"
  ],
  ...
  "plugins": [
    ...
    "prettier"
  ],
  "rules": {
    ...
    "prettier/prettier": "error",
    "@typescript-eslint/explicit-module-boundary-types": "off",
    "react/jsx-one-expression-per-line": "off",
    "no-use-before-define":"off"

   },
  ...
}
```

Create a file `prettier.config.js` in the root of the project.

`prettier.config.js`

```js
module.exports = {
    singleQuote: true,
    trailingComma: 'all',
    allowParens: 'avoid',
}
```

Go to the `.src/index.tsx` and `./src/reportWebVitals.ts` files and save the files for them to be formatted by Prettier.

`yarn start`
