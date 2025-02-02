# Fontsource Newsreader

[![npm (scoped)](https://img.shields.io/npm/v/@fontsource/newsreader?color=brightgreen)](https://www.npmjs.com/package/@fontsource/newsreader) [![Generic badge](https://img.shields.io/badge/fontsource-passing-brightgreen)](https://github.com/fontsource/fontsource) [![Monthly downloads](https://badgen.net/npm/dm/@fontsource/newsreader)](https://github.com/fontsource/fontsource) [![Total downloads](https://badgen.net/npm/dt/@fontsource/newsreader)](https://github.com/fontsource/fontsource) [![GitHub stars](https://img.shields.io/github/stars/fontsource/fontsource.svg?style=social&label=Star)](https://github.com/fontsource/fontsource/stargazers)

The CSS and web font files to easily self-host the “Newsreader” font. Please visit the main [Fontsource monorepo](https://github.com/fontsource/fontsource) to view more details on this package.

## Installation

Fontsource assumes you are using a bundler, such as Webpack, to load in CSS. Solutions like [CRA](https://create-react-app.dev/), [Gatsby](https://www.gatsbyjs.org/) and [Next.js](https://nextjs.org/) are prebuilt examples that are compatible.

```javascript
yarn add @fontsource/newsreader // npm install @fontsource/newsreader
```

Then within your app entry file or site component, import it in. For example in Gatsby, you could choose to import it into a layout template (`layout.js`), page component (`index.js`), or `gatsby-browser.js`.

```javascript
import "@fontsource/newsreader" // Defaults to weight 400.
```

Fontsource allows you to select weights and even individual styles, allowing you to cut down on payload sizes to the last byte! Utilizing the CSS unicode-range selector, all language subsets are accounted for.

```javascript
import "@fontsource/newsreader/500.css" // Weight 500.
import "@fontsource/newsreader/900-italic.css" // Italic variant.
```

Alternatively, the same solutions could be imported via SCSS!

```scss
@import "~@fontsource/newsreader/index.css"; // Weight 400.
@import "~@fontsource/newsreader/300-italic.css";
```

For more advanced setups, you can use our highly customisable Sass mixins that can modify many of the existing @font-face variables.

```scss
@import "~@fontsource/newsreader/scss/mixins";

// Uses a unicode-range map to automatically generate multiple @font-face rules.
@include fontFace(
  $weight: 500,
  $display: fallback,
  $fontDir: "~@fontsource/newsreader/files"
);

// Fully customisable single @font-face mixin.
@include fontFaceCustom(
  $weight: 600,
  $display: optional,
  $woff2Path: "#{$fontDir}/custom-file.woff2",
  $unicodeRange: false
);
// More options available in link below.
```

We also have default variables that you can use!

```scss
@import "~@fontsource/newsreader/scss/mixins";

$style: italic;

@include fontFace($weight: 500);
@include fontFace($weight: 600);

// Applies italic to both @includes.
```

You can see all of the existing inputtable mixin variables [here](https://github.com/fontsource/fontsource/tree/master/packages/newsreader/scss/mixins.scss).

_These examples may not reflect actual compatibility. Please refer below._

Supported variables:

- Weights: `[200,300,400,500,600,700,800]`
- Styles: `[italic,normal]`

Finally, you can reference the font name in a CSS stylesheet, CSS Module, or CSS-in-JS.

```css
body {
  font-family: "Newsreader";
}
```

## Variable Fonts

This particular typeface supports [variable fonts](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Fonts/Variable_Fonts_Guide).

Begin by importing both the variable and fallback font for non-compatible browsers.

```js
import "@fontsource/newsreader/400.css" // Weight 400.
```

Select either a stripped down weights only variant of the font or a full feature variant that contains all the variable axes.

```js
import "@fontsource/newsreader/variable.css" // Contains ONLY variable weights and no other axes.
import "@fontsource/newsreader/variable-italic.css" // Italic variant.
// Or
import "@fontsource/newsreader/variable-full.css" // This contains ALL variable axes. Font files are larger.
import "@fontsource/newsreader/variable-full-italic.css" // Italic variant.
```

Note a `full` or `italic` variant may NOT exist if there are no additional axes other than wght and/or ital. You can check the available axes [here](https://fonts.google.com/variablefonts).

Followed by the CSS using the @supports tag, which checks whether the browser is capable of utilising variable fonts. Fallback fonts and their relevant CSS should be used outside the block, whilst all variable options should be used within the @supports block and utilising the font-variation-settings tag.

```css
h1 {
  font-family: Newsreader;
  font-weight: 400;
}

@supports (font-variation-settings: normal) {
  h1 {
    font-family: NewsreaderVariable;
    font-variation-settings: "wght" 400;
  }
}
```

For Sass mixins, please use fontFaceVariable() and fontFaceVariableCustom which introduces the new $type variable to choose between "wghtOnly" and "full".

_To view the available variable axes that may be included in the font, click [here](https://fonts.google.com/variablefonts). The meanings of all axes and the restrictions associated with them are explained there._

## Additional Options

In the rare case you need to individually select a language subset and not utilize the CSS unicode-range selector, you may specify the import as follows. This is especially not recommended for languages, such as Japanese, with a large amount of characters.

```javascript
import "@fontsource/newsreader/latin-ext.css" // All weights with normal style included.
import "@fontsource/newsreader/cyrillic-ext-500.css" // Weight 500 with normal style.
import "@fontsource/newsreader/greek-900-italic.css" // Italic variant.
```

- Supported subsets: `[latin,latin-ext,vietnamese]`

## Licensing

It is important to always read the license for every font that you use.
Most of the fonts in the collection use the SIL Open Font License, v1.1. Some fonts use the Apache 2 license. The Ubuntu fonts use the Ubuntu Font License v1.0.

[Google Fonts License Attributions](https://fonts.google.com/attribution)

## Other Notes

Font version (provided by source): `v4`.

Feel free to star and contribute new ideas to this repository that aim to improve the performance of font loading, as well as expanding the existing library we already have. Any suggestions or ideas can be voiced via an [issue](https://github.com/fontsource/fontsource/issues).
