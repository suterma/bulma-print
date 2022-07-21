# bulma-print

![License](https://img.shields.io/github/license/suterma/bulma-print.svg)
![GitHub All Releases](https://img.shields.io/github/downloads/suterma/bulma-print/total.svg)
![Release](https://img.shields.io/github/release/suterma/bulma-print.svg)
![Language](https://img.shields.io/github/languages/top/suterma/bulma-print.svg)
[![](https://data.jsdelivr.com/v1/package/npm/bulma-print/badge)](https://www.jsdelivr.com/package/npm/bulma-print)


Extends the [Bulma CSS framework](https://bulma.io/) with additional classes and styles suitable for printing.

As with Bulma, you can either use the pre-compiled `.css` file or install the `.sass` files from the NPM package.

## Using a CDN (without installation)

Import the CSS file directly from [jsDelivr](https://www.jsdelivr.com/package/npm/bulma-print). just after Bulma:

```html
<!--index.html-->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@0.9.4/css/bulma.min.css"><!--the Bulma CSS-->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma-print@1.0.0/css/bulma-print.css"><!--add bulma-print.css-->
```

## Installing from NPM 

```sh
npm install bulma-print --save-dev
```
_or_

```sh
yarn add bulma-print --dev
```

Now you can either either use the pre-compiled `bulma-print.css` file:

```html
<!--index.html-->
<link rel="stylesheet" href="css/main.css"><!--the Bulma CSS-->
<link rel="stylesheet" href="./node_modules/bulma-print/css/bulma-print.css"><!--add bulma-print.css-->
```

_or_

include the `bulma-print.scss` file into your Sass chain:

```scss
//main.scss
@import "../node_modules/bulma/bulma"; //the bulma.scss
@import "../node_modules/bulma-print/bulma-print"; //add bulma-print.scss
```

Your [Sass](https://sass-lang.com/) compiler will then process `bulma-print.scss` alongside your project's other Sass files into the CSS file, from where you can use it.

## How to use

To arrange the print layout of your pages, you can add the following classes to your HTML:

| Add on class | Description |
| ------------- | ------------- |
| `is-hidden-print` | Hides the element on the printed page |
| `is-print-only` | Hides the element on non-print media |
| `is-not-linked-print` | Suppresses the (added by default) printout of the hyperlink URL |
| `has-page-break-after` | Adds a page break after the element |
| `has-page-break-before` | Adds a page break before the element |
| `is-together-print` | Avoids page breaks inside the element |

The class names follow the naming pattern from the visibility helpers, as per the [Bulma documentation](https://bulma.io/documentation/helpers/visibility-helpers/).

### Examples

Not printing the navbar
```html
    <nav id="navbar" class="bd-navbar navbar is-hidden-print">
    <!-- navbar content... -->
    </nav>
```

Adding a special information, only for printouts
```html
    <section class="hero is-print-only">
        <!-- About this printed document... -->
    </section>
```

Adding a page break before a header
```html
    <h3 class="has-page-break-before">Try it out!</h3>
```

### Further considerations

#### Printed links

Bulma-print will by default add the hyperlink URL (`href`) after any `a` (anchor) element. Otherwise, hyperlinks are not usable from  print media. If you do not like this for a link, you can suppress this via the specific marker class `is-not-linked-print`.

#### Page breaks

Print media has the additional concept of pages. The page breaks can be controlled and specifically set, for example you can add `has-page-break-before` on `h1` elements, to add a page break beforehand, to produce a more expected layout on print media. Also, for enumerations like lists or with tables, you might want to keep these on the same page, and can thus use `is-together-print` on the outermost element, like `ul` or `table`.

#### Responsive size

For printing, Bulma by default uses the layout styles as for their "tablet" screen size. See the [Bulma breakpoint documentation](https://bulma.io/documentation/overview/responsiveness/#breakpoints). This package does not change this.

#### Automatic color adjustments

Any browser may try to optimize the printed colors as it sees fit, and most browsers do. See the documentation about the [`print-color-adjust` CSS property](https://developer.mozilla.org/docs/Web/CSS/print-color-adjust) for more information. Bulma-print does not change this value. You may want to add your custom styles to produce the exact output you like.

## What's included

This package contains:

  - a main Scss file, `bulma-print.scss` which includes the styles for the above classes.
  - Additional, experimental styles in the `experimental` folder. Use with caution.
  - a pre-compiled .css file, if you do not want to build from .scss

## Build

Use `npm run` to show all available commands:

```sh
  css-deploy
    npm run css-build && npm run css-postcss
  css-build
    sass --no-source-map bulma-print.scss:css/bulma-print.css
  css-postcss
    postcss --use autoprefixer --output css/bulma-print.css css/bulma-print.css

  //Build continuously
  css-watch
    npm run css-build -- --watch    
```

## About Bulma-print

Currently, Bulma is missing print-specific styling. It has been reported as https://github.com/jgthms/bulma/issues/721, and until 
it's implemented, this package may serve as a stand-in.

## About Bulma

If you want to learn more about Bulma, follow these links: [Bulma homepage](http://bulma.io) and [Documentation](http://bulma.io/documentation/overview/start/).

## Copyright and license

Code copyright by Marcel Suter. Code released under [the MIT license](https://github.com/suterma/bulma-print/blob/main/LICENSE).