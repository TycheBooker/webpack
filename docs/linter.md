# Linter Configuration

This boilerplate uses [ESLint](https://eslint.org/) as the linter, and uses the [Recommended](https://github.com/eslint/eslint/blob/master/conf/eslint-recommended.js) preset with some small customizations.

If you are not happy with the default linting rules, you can overwrite individual rules in `.eslintrc.js`. For example, you can add the following rule to enforce semicolons instead of omitting them:

  ``` js
  // .eslintrc.js
  "semi": [2, "always"]
  ```

