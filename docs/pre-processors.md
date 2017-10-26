# Pre-Processors

This boilerplate has pre-configured CSS extraction for most popular CSS pre-processors including LESS, SASS, Stylus, and PostCSS. The SassLoader and NodeSass have already been added.
To use any other pre-processor, you need to install the appropriate webpack loader and its dependencies for it.

### Using Pre-Processors inside Components

Once installed, you can use the pre-processors inside your `*.vue` components using the `lang` attribute on `<style>` tags:

``` html
<style lang="scss">
/* write SASS! */
</style>
```

### A note on SASS syntax

- `lang="scss"` corresponds to the CSS-superset syntax (with curly braces and semicolons).
- `lang="sass"` corresponds to the indentation-based syntax.

### PostCSS

Styles in `*.vue` files are piped through PostCSS by default, so you don't need to use a specific loader for it. You can simply add PostCSS plugins you want to use in `build/webpack.base.conf.js` under the `vue` block:

``` js
// build/webpack.base.conf.js
module.exports = {
  // ...
  vue: {
    postcss: [/* your plugins */]
  }
}
```

See [vue-loader's related documentation](http://vuejs.github.io/vue-loader/en/features/postcss.html) for more details.

### Standalone CSS Files

To ensure consistent extraction and processing, it is recommended to import global, standalone style files from your root `App.vue` component, for example:

``` html
<!-- App.vue -->
<style src="./styles/global.less" lang="less"></style>
```
or import them into the style tag:

``` html
<!-- App.vue -->
<style lang="scss">
@import './styles/base.scss';
</style>
```

Note you should probably only do this for the styles written by yourself for your application. For existing libraries e.g. Bootstrap or Semantic UI, you can place them inside `/static` and reference them directly in `index.html`. This avoids extra build time and also is better for browser caching. (See [Static Asset Handling](static.md))

### SCSS Includes

The Scss loader has been preconfigured to include all scss partial files located in `/styles/includes/` into all scss blocks. To avoid repeated css code, these files shouldn't include anything but pure scss functions like mixins and vars.
