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

Indent all [block content](http://www.w3.org/TR/CSS21/syndata.html#block), that is rules within rules as well as declarations, so to reflect hierarchy and improve understanding.

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

**Separate selectors, declarations and rules by new lines.**

```css
/* Not recommended */
h1, h2, h3 {
  font-weight: normal;  line-height: 1.2;
}
p {
  margin-bottom: 1.5em;
}
@media only screen {
  h1 {
    color: #333;
  }
}

/* Recommended */
h1,
h2,
h3 {
  font-weight: normal;
  line-height: 1.2;
}

p {
  margin-bottom: 1.5em;
}

@media only screen {
  
  h1 {
    color: #333;
  }
  
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

#### Delimiters

#### Prefixes

#### Type selectors

### Properties

#### Shorthand notation

### Values

#### 0 and units

#### Leading 0s

#### Hexadecimal notation

#### Multiple comma-separated values

### Quotation marks

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
