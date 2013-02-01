# CSS style guide

The following document outlines a reasonable style guide for CSS development. These guidelines strongly encourage the use of existing, common, sensible patterns. They should be adapted as needed to create your own style guide.

## Table of contents

1. [General principles](#1-general-principles)
2. [Formatting](#2-formatting)
3. [Comments](#3-comments)

[Acknowledgements](#acknowledgements)

[Other CSS style guides](#other-css-style-guides)

## 1. General principles

### Consistency

**Be consistent.** If you’re editing code, take a few minutes to look at the code around you and determine its style. If they use spaces around all their arithmetic operators, you should too. If their comments have little boxes of hash marks around them, make your comments have little boxes of hash marks around them too.

The point of having style guidelines is to have a common vocabulary of coding so people can concentrate on what you’re saying rather than on how you’re saying it. If code you add to a file looks drastically different from the existing code around it, it throws readers out of their rhythm when they go to read it. Avoid this.

### Validity

**Unless dealing with CSS validator bugs or requiring proprietary syntax, use valid CSS code.** Use tools such as the [W3C CSS validator](http://jigsaw.w3.org/css-validator/) to test. Using valid CSS is a measurable baseline quality attribute that allows to spot CSS code that may not have any effect and can be removed, and that ensures proper CSS usage.

## 2. Formatting

### Capitalization

**Use only lowercase.** This applies to selectors, properties and property values (with the exception of strings).

```css
/* Not recommended */
UL,
.HeAdER {
  COLOR: #3AF;
}

/* Recommended */
ul,
.header {
  color: #3af;
}
```

### Indentation and whitespace

**Indent by two spaces at a time.** Don’t use tabs or mix tabs and spaces for indentation.

```css
/* Not recommended */
.example {
	       background: #fff;
     color: #333;
}

/* Recommended */
.example {
  background: #fff;
  color: #333;
}
```

**Indent all [block content](http://www.w3.org/TR/CSS21/syndata.html#block)**, that is rules within rules as well as declarations, so to reflect hierarchy and improve understanding.

```css
/* Not recommended */
@media only screen and (min-width: 80em) {

html {
  font-size: 1.125em;
}

}

/* Recommended */
@media only screen and (min-width: 80em) {

  html {
    font-size: 1.125em;
  }

}
```

**Remove trailing whitespaces.** Trailing whitespaces are unnecessary and can complicate diffs.

```css
/* Not recommended (trailing whitespaces marked as “_”) */
.example {__
  background: #fff;_____
  color: #333;__
}

/* Recommended */
.example {
  background: #fff;
  color: #333;
}
```

### Selector, declaration and rule separation

Separate selectors and declarations by new lines.

```css
/* Not recommended */
h1, h2, h3 {
  font-weight: normal;  line-height: 1.2;
}

/* Recommended */
h1,
h2,
h3 {
  font-weight: normal;
  line-height: 1.2;
}
```

Separate rules by new lines and always put a line between rules.

```css
/* Not recommended */
html {
  background: #fff;
} body {
  margin: auto;
  width: 50%;
}
h1 {
  font-size: 2em;
}

/* Recommended */
html {
  background: #fff;
}

body {
  margin: auto;
  width: 50%;
}

h1 {
  font-size: 2em;
}
```

### Declaration order

**Alphabetize declarations.** Put declarations in alphabetical order in order to achieve consistent code in a way that is easy to remember and maintain. Ignore vendor-specific prefixes for sorting purposes. However, multiple vendor-specific prefixes for a certain CSS property should be kept sorted (e.g. `-moz` prefix comes before `-webkit`).

```css
/* Not recommended */
.box {
  text-indent: 2em;
  background: #f5f5f5;
  -webkit-transform: rotate(-2deg);
  -moz-transform: rotate(-2deg);
  -o-transform: rotate(-2deg);
  -ms-transform: rotate(-2deg);
  transform: rotate(-2deg);
  color: #000;
  border: 1px solid;
  text-align: center;
  border-radius: 4px;
}

/* Recommended */
.box {
  background: #f5f5f5;
  border: 1px solid;
  border-radius: 4px;
  color: #000;
  text-align: center;
  text-indent: 2em;
  -moz-transform: rotate(-2deg);
  -ms-transform: rotate(-2deg);
  -o-transform: rotate(-2deg);
  -webkit-transform: rotate(-2deg);
  transform: rotate(-2deg);
}
```

### IDs and classes

#### Naming

**Use meaningful or generic ID and class names.** Instead of presentational or cryptic names, always use ID and class names that reflect the purpose of the element in question, or that are otherwise generic. Names that are specific and reflect the purpose of the element should be preferred as these are most understandable and the least likely to change. Generic names are simply a fallback for elements that have no particular or no meaning different from their siblings. They are typically needed as “helpers”. Using functional or generic names reduces the probability of unnecessary document or template changes.

```css
/* Not recommended: meaningless */
#yee-1901 {}

/* Not recommended: presentational */
.button-green {}
.clear {}

/* Recommended: specific */
.gallery {}
.login {}
.video {}

/* Recommended: generic */
.aux {}
.alt {}
```

**Use ID and class names that are as short as possible but as long as necessary.** Try to convey what an ID or class is about while being as brief as possible. Using ID and class names this way contributes to acceptable levels of understandability and code efficiency.

```css
/* Not recommended */
#navigation {}
.atr {}

/* Recommended */
#nav {}
.author {}
```

#### Delimiters

**Separate words in ID and class names by a hyphen.** Do not concatenate words and abbreviations in selectors by any characters (including none at all) other than hyphens, in order to improve understanding and scannability.

```css
/* Not recommended: does not separate the words “demo” and “image” */
.demoimage {}

/* Not recommended: uses underscore instead of hyphen */
.error_status {}

/* Recommended */
#video-id {}
.ads-sample {}
```

#### Type selectors

**Avoid qualifying ID and class names with type selectors.** Unless necessary (for example with helper classes), do not use element names in conjunction with IDs or classes. Avoiding unnecessary ancestor selectors is useful for [performance reasons](http://www.stevesouders.com/blog/2009/06/18/simplifying-css-selectors/).

```css
/* Not recommended */
ul#example {}
div.error {}

/* Recommended */
#example {}
.error {}
```

### Properties

#### Shorthand notation

**Use shorthand properties where possible.** CSS offers a variety of [shorthand](http://www.w3.org/TR/CSS21/about.html#shorthand) properties (like `font`) that should be used whenever possible, even in cases where only one value is explicitly set. Using shorthand properties is useful for code efficiency and understandability.

```css
/* Not recommended */
.example {
  border-top-style: none;
  font-family: palatino, georgia, serif;
  font-size: 100%;
  line-height: 1.6;
  margin-bottom: 2em;
  margin-left: 1em;
  margin-right: 1em;
  margin-top: 0;
}

/* Recommended */
.example {
  border-top: 0;
  font: 100%/1.6 palatino, georgia, serif;
  margin: 0 1em 2em;
}
```

### Values

#### “0” and units

**Omit unit specification after “0” values** unless they are required.

```css
/* Not recommended */
* {
  margin: 0px;
  padding: 0px;
}

.box {
  border-top: 0px;
}

/* Recommended */
* {
  margin: 0;
  padding: 0;
}

.box {
  border-top: 0;
}
```

#### Leading “0”s

**Omit leading “0”s in values.** Do not put “0”s in front of values or lengths between -1 and 1.

```css
/* Not recommended */
small {
  font-size: 0.875em;
}

/* Recommended */
small {
  font-size: .875em;
}
```

#### Hexadecimal notation

**Use 3 character hexadecimal notation where possible.** For color values that permit it, 3 character hexadecimal notation is shorter and more succinct.

```css
/* Not recommended */
p {
  color: #4455aa;
}

/* Recommended */
p {
  color: #45a;
}
```

#### Multiple comma-separated values

**Multiple comma-separated values for one property should be separated by either a space or a newline**, including within `rgb()`, `rgba()`, `hsl()` and `hsla()`. Newlines should be used for lengthier multi-part values such as those for shorthand properties like `box-shadow` and `text-shadow`. Each subsequent value after the first should then be on a new line, indented to the same level as the selector and then spaced over to left-align with the previous value.

```css
/* Not recommended */
.example {
  font-family: arial,sans-serif;
  text-shadow: 0 3px 0 #b2a98f, 0 14px 10px rgba(0,0,0,.15), 0 24px 12px rgba(0,0,0,.12), 0 34px 30px rgba(0,0,0,.12);
}

/* Recommended */
.example {
  font-family: arial, sans-serif;
  text-shadow: 0 3px 0 #b2a98f,
               0 14px 10px rgba(0, 0, 0, .15),
               0 24px 12px rgba(0, 0, 0, .12),
               0 34px 30px rgba(0, 0, 0, .12);
}
```

### Quotation marks

**Use single quotation marks for attribute selectors and property values.** Use single (`''`) rather than double (`""`) quotation marks for attribute selectors or property values. Do not use quotation marks in URI values (`url()`). Exception: If you do need to use the `@charset` rule, use double quotation marks—single quotation marks are [not permitted](http://www.w3.org/TR/CSS21/syndata.html#charset).

```css
/* Not recommended */
html {
  background: #fff url("img/bg.png") repeat 0 0;
  font-family: "open sans", arial, sans-serif;
}

input[type="search"] {
  margin-left: 1em;
}

/* Recommended */
html {
  background: #fff url(img/bg.png) repeat 0 0;
  font-family: 'open sans', arial, sans-serif;
}

input[type='search'] {
  margin-left: 1em;
}
```

## 3. Comments

## Acknowledgements

## Other CSS style guides

- [BBC](http://www.bbc.co.uk/guidelines/futuremedia/technical/css.shtml)
- [CSS Wizardry](http://csswizardry.com/2012/04/my-html-css-coding-style/)
- [GitHub](https://github.com/styleguide/css)
- [Google](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)
- [Idiomatic CSS](https://github.com/necolas/idiomatic-css)
- [SMACSS](http://smacss.com/)
- [ThinkUp](https://github.com/ginatrapani/ThinkUp/wiki/Code-Style-Guide:-CSS)
- [WordPress](http://make.wordpress.org/core/handbook/coding-standards/css/)
