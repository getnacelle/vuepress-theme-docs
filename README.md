# Nacelle Vuepress Documentation Theme

Theme used for the [Nacelle documentation](https://docs.getnacelle.com/).

## Getting Started

### Install the theme

```
npm i @nacelle/vuepress-theme-docs -S
```

### Add to Vuepress config

In your Vuepress theme config:

```js
module.exports = {
  // default vuepress config settings
  theme: '@nacelle/vuepress-theme-docs',
  themeConfig: {
    // vuepress default theme settings
    logo: 'path/to/header-logo.svg',
    footerLogo: 'path/to/footer-logo.svg',
  },
}
```

## Development

After cloning the theme project, navigate to the documentation project. Once there, link the cloned theme project. Example:

```
cd docs-project
npm link ../path/to/theme
```

You can now start the documentation project using the Nacelle theme. More information about theme inheritance and development can be found [here](https://vuepress.vuejs.org/theme/inheritance.html).
