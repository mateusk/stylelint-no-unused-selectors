# @mknelsen/stylelint-no-unused-selectors

[![npm version](https://img.shields.io/npm/v/@mknelsen%2Fstylelint-no-unused-css-selectors.svg)](https://www.npmjs.com/package/@mknelsen/stylelint-no-unused-css-selectors)
[![license](https://img.shields.io/npm/l/@mknelsen%2Fstylelint-no-unused-css-selectors.svg)](https://www.npmjs.com/package/@mknelsen/stylelint-no-unused-css-selectors)

A Stylelint plugin that detects and flags unused CSS selectors in your HTML, Vue, and other template files, helping you keep your codebase clean and optimized.

## 🌟 Features

- Detects unused CSS selectors in HTML, Vue, and other templating languages.
- Supports nested CSS selectors and dynamic class bindings in Vue.
- Allows you to configure patterns of selectors to ignore (e.g., framework-specific classes).
- Works seamlessly with popular frameworks and setups like Vue.js, Nuxt, and others.

## 📦 Installation

Install the plugin as a development dependency using NPM or Yarn:

```bash
npm install @mknelsen/stylelint-no-unused-selectors --save-dev
# or
yarn add @mknelsen/stylelint-no-unused-selectors --dev
```

## 🚀 Usage

To use this plugin, add it to your Stylelint configuration:

### Basic Configuration

In your .stylelintrc.json, add the plugin to the `plugins` array:

```json
{
  "plugins": ["@mateusk/stylelint-no-unused-selectors"],
  "rules": {
    "custom/selector-no-unused": [
      "severity": "warning",
      {
        "ignore": ["^\\.v-", "^#app$", "^\\.some-pattern"]
      }
    ]
  }
}
```

The following options are available:

- `severity`: The severity level of the rule. Can be one of "error", "warning", or "off". Defaults to "error".
- `ignore`: An array of regular expressions that match selectors to ignore.

### Example Vue Component

This plugin is capable of detecting selectors used dynamically in Vue components:

```vue
<script setup>
const isActive = ref(true);
</script>

<template>
  <div :class="{ 'my-class': isActive }"></div>
</template>

<style scoped>
.my-class {
  color: red;
}

/* This selector would be flagged as unused */
.unused-class {
  color: blue;
}
</style>
```

## ⚙️ Configuration Options

### Ignored Selectors

You can specify patterns for selectors that should not be flagged as unused, even if they are not detected in the template:

```json
{
  "rules": {
    "custom/selector-no-unused": [
      "severity": "warning",
      {
        "ignore": ["^\\.v-", "^#app$", "^\\.some-pattern"]
      }
    ]
  }
}
```

This is especially useful for ignoring framework-specific selectors that may be applied globally or dynamically.

## 🧪 Examples

### Basic HTML Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .used {
        color: green;
      }
      .unused {
        color: red;
      }
    </style>
  </head>
  <body>
    <div class="used">Hello, World!</div>
  </body>
</html>
```

If you run Stylelint on this file, it will flag .unused as an unused CSS selector.

### Nested selectors

```css
.container {
  display: flex;
  .item {
    margin: 5px;
    &.active {
      color: blue;
    }
  }
}
```

The plugin correctly recognizes nested CSS selectors and will not incorrectly flag .item.active if it is dynamically added via Vue.

## 🛠️ Development & Contribution

Contributions are welcome! If you’d like to contribute, please:

1. Fork this repository.
2. Create a new branch (git checkout -b feature/your-feature).
3. Commit your changes (git commit -am 'Add a new feature').
4. Push to your branch (git push origin feature/your-feature).
5. Create a pull request.

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🏷️ Changelog

See Releases for the version history of this project.
