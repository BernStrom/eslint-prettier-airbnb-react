# Installation

1. Navigate to your app directory where you want to include this style configuration.

   ```bash
   cd my-react-app
   ```

2. Run this command inside your app's root directory. Note: this command executes the `eslint-prettier-config.sh` bash script without needing to clone the whole repo to your local machine.

   ```bash
   exec 3<&1;bash <&3 <(curl https://raw.githubusercontent.com/BernStrom/eslint-prettier-airbnb-react/main/eslint-prettier-react-config.sh 2> /dev/null)
   ```
   For convenience, you could also assign the above command to an `alias` of your choice in your shell profile (`bash_profile, .zshrc`) 👇
    
      ```bash
      alias eslint-init="exec 3<&1;bash <&3 <(curl https://raw.githubusercontent.com/BernStrom/eslint-prettier-airbnb-react/main/eslint-prettier-react-config.sh 2> /dev/null)"
      ```

3. Make selections for your preference of package manager (npm or yarn), file format (.js or .json), max-line size, and trailing commas (none, es5, all).

4. Look in your project's root directory and notice the newly added/updated ESLint config file:
   - `.eslintrc.js` (or `.eslintrc.json`)

# Packages

### Main Packages

1. [ESlint](https://eslint.org/)
2. [Prettier](https://prettier.io/)

### Airbnb Configuration

1. [eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb)
   - This package provides Airbnb's .eslintrc as an extensible shared config.
2. [eslint-plugin-jsx-a11y](https://github.com/evcohen/eslint-plugin-jsx-a11y) (Peer Dependency)
   - Static AST checker for accessibility rules on JSX elements.
3. [eslint-plugin-react](https://github.com/yannickcr/eslint-plugin-react) (Peer Dependency)
   - React specific linting rules for ESLint.
4. [eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks)
   - Enforces the [Rules of Hooks](https://reactjs.org/docs/hooks-rules.html).
5. [eslint-plugin-import](https://www.npmjs.com/package/eslint-plugin-import) (Peer Dependency)
   - Support linting of ES2015+ (ES6+) import/export syntax, and prevent issues with misspelling of file paths and import names.
6. [babel-eslint](https://github.com/babel/babel-eslint)
   - A wrapper for Babel's parser used for ESLint.
   - Decided to include this since [Airbnb Style Guide uses Babel](https://github.com/airbnb/javascript#airbnb-javascript-style-guide-).

### ESlint, Prettier Integration

1. [eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier)
   - Runs Prettier as an ESLint rule and reports differences as individual ESLint issues.
2. [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier)
   - Turns off all rules that are unnecessary or might conflict with Prettier.

# Created Configuration Files

Once files are created, you may edit to your liking.

### eslintrc(.js/.json)

- [Configuration info for ESLint](https://eslint.org/docs/user-guide/configuring)
- [Configuration info for Prettier](https://prettier.io/docs/en/configuration.html)


```
{
  "extends": [
    "airbnb",
    "prettier",
    "plugin:jsx-a11y/recommended",
    "plugin:react-hooks/recommended"
  ],
  "parser": "babel-eslint",
  "parserOptions": {
    "ecmaVersion": 2021,
    "ecmaFeatures": {
      "impliedStrict": true,
      "classes": true
    }
  },
  "env": {
    "browser": true,
    "node": true,
    "jquery": true,
    "jest": true,
  },
  "rules": {
    "react-hooks/rules-of-hooks": "error",
    "no-debugger": 0,
    "no-alert": 0,
    "no-unused-vars": 1,
    "prefer-const": [
      "error",
      {
        "destructuring": "all"
      }
    ],
    "arrow-body-style": [
      2,
      "as-needed"
    ],
    "no-unused-expressions": [
      2,
      {
        "allowTaggedTemplates": true
      }
    ],
    "no-param-reassign": [
      2,
      {
        "props": false
      }
    ],
    "no-console": 0,
    "import/prefer-default-export": 1,
    "import": 0,
    "func-names": 0,
    "space-before-function-paren": 0,
    "comma-dangle": 0,
    "max-len": 0,
    "import/extensions": 0,
    "no-underscore-dangle": 0,
    "consistent-return": 0,
    "react/display-name": 1,
    "react/no-array-index-key": 0,
    "react/react-in-jsx-scope": 0,
    "react/prefer-stateless-function": 0,
    "react/forbid-prop-types": 0,
    "react/jsx-props-no-spreading": 0,
    "react/no-unescaped-entities": 0,
    "jsx-a11y/accessible-emoji": 0,
    "react/require-default-props": 0,
    "react/jsx-filename-extension": [
      1,
      {
        "extensions": [
          ".js",
          ".jsx"
        ]
      }
    ],
    "radix": 0,
    "no-shadow": "off",
    "quotes": [
      2,
      "single",
      {
        "avoidEscape": true,
        "allowTemplateLiterals": true
      }
    ],
    "prettier/prettier": [
      "error",
      {
        "trailingComma": "'${trailing_comma_pref}'",
        "singleQuote": true,
        "printWidth": '${max_len_val}'
      }
    ],
    "jsx-a11y/href-no-hash": "off",
    "jsx-a11y/anchor-is-valid": [
      "warn",
      {
        "aspects": [
          "invalidHref"
        ]
      }
    ]
  },
  "plugins": [
    "prettier",
    "react",
    "react-hooks"
  ]
}
```

# License [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
This project is licensed under the terms of the MIT license. For more information, please refer to the license [documentation](LICENSE.md).