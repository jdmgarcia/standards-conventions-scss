## pkStyle: _Standards_ and _Conventions_.

> Standards, conventions and good practices of nomenclatures, file structures, class names, programming styles, etc.

------

__Table of Contents:__

1. Comments into .SCSS files.
2. Naming.
    1. Folders and files
    2. Functions, mixins, placeholders, arguments and variables.
    3. Classes.
    4. Value format.
    5. Developing.
3. SASS code.
    1. Properties.
    2. Media queries.
    3. Mixins and functions.
4. Placeholders.
5. Extensions.
    


------

##### 1. Comments into .SCSS files.

All comments in a SCSS file must be in English, concise and easy to understand.
All comments online must start with `//`, you should not use `/* .. */`.
All comments on more than one line must start with `/*` and end with `*/`, starting with `*` on the intermediate lines.
`/* .. */` is reserved for stylelint-disable or stylelint-enable.

Examples:

```scss 
// Separation unit of for fields by row
.form-group {
    width: 100%;

    + .form-group {
        margin-top: $spacer;
    }
}
```

```scss
/*
*  Makes visuallyhidden items visible again
*/

@mixin visible() {
    ...
}
```

```scss
/* stylelint-disable color-hex-length */
$black: #000000 !default;
/* stylelint-enable color-hex-length */
$dove-gray: #5d5d5d !default;
```


##### 2. Naming.

> Naming [BEM](http://bem.info/).

**Important:** Any name will be generated starting from the most generic to the most specific word. Where the generic can be a common noun that will prefix multiple nominations.


**2.1. Folders and files**

They must begin with a lowercase letter and if the name of the folder or file is composed of several words, they will be separated by hyphens '-', using **kebab-case**.


**2.2. Functions, mixins, placeholders, arguments and variables.**

The names of the functions, mixins and placeholders: begin with a lowercase letter and if the name is composed of several words, they will be separated by hyphens '-', using **kebab-case**.

The names of the arguments (parameters of mixins and functions): **kebab-case**.


**2.3. Classes.**

They must be named in lowercase by separating each word with a normal hyphen "-", using **kebab-case**.

```scss
.class-name {
    { css-rules }
}
```

**2.4. Value format.**

**Colors:** if they are in hexadecimal they must be named with their six lowercase characters.

```scss
.rule-name {
    property-name: #rrggbb;  // example: background-color: #fabada;
}
```

> Convention accepted by Firebug, inspector of elements of Google Chrome and Bootstrap, among others.

For the value 0 of a property: when you want to indicate that it has a value of 0, for example, 0px or 0rem, it must be specified without units.

```scss
.rule-name {
    property-name: 0;  // example: padding-left: 0;
}
```
> Convention specified in [CSS Lint](http://csslint.net/)


**2.5. Developing.**

To mark a piece of code that must be reviewed, its operation is unknown or is under development, it must be marked with the comment: `//TODO`. Example:

```scss
//TODO: https://github.com/packlink-dev/giger/issues/129
.snack-bar {
    ...
}
```


##### 3. SASS code.

**3.1. Properties.**

All properties within a rule must end with a semicolon, also the last one.

```scss
.rule-name {
    property-name-1: property-value-1;
    property-name-2: property-value-2;
    ..
    property-name-n: property-value-n;
}
```

There should not be more than one rule per line.

```scss
.rule-name-1,
.rule-name-2,
..
.rule-name-n {
    property-name-1: property-value-1;
    property-name-2: property-value-2;
    ..
    property-name-n: property-value-n;
}
```

The order of the rules should follow, as far as possible, the following order:

* Layout Properties (`position`, `float`, `clear`, `display`)
* Box Model Properties (`width`, `height`, `margin`, `padding`)
* Visual Properties (`color`, `background`, `border`, `box-shadow`)
* Typography Properties (`font-size`, `font-family`, `text-align`, `text-transform`)
* Misc Properties (`cursor`, `overflow`, `z-index`)


**3.2. Media queries.**

The properties dependent on _media queries_ will be included within each corresponding rule or class in their own nesting, never including other classes and their properties so that the _responsive_ is as atomic as possible and independent of other rules or classes. For the declaration of _media queries_ we must use the mixinn __*media-query*__. For example:

```scss
.rule-name {
    property-name-1: property-value-1;
    property-name-2: property-value-2;
    ..
    property-name-n: property-value-n;

    @include media-query(media) {
        property-name-1: property-value-1;
        property-name-2: property-value-2;
        ..
        property-name-n: property-value-n;
    }
}
```

> To see the possible values of **media**, see the mixin **@mixin media-query($media)**.


**3.3. Mixins and functions.**

**Important:** __*A mixin that has no arguments, or that is always used with the default values ​​of its arguments, is a placeholder.*__

Mixins and functions, both statement and call, should be written without separation between the name and the argument list:

```scss
// Statement
@mixin mixin-name($argument-name-1, $argument-name-2..$argument-name-n) {
    {mixin body}
}
// Statement
@function function-name($argument-name-1, $argument-name-2..$argument-name-n) {
    {function body}
}

// Mixin usage
@include mixin-name($argument-name-1, $argument-name-2..$argument-name-n);

// Function usage
function-name($argument-name-1, $argument-name-2..$argument-name-n);
```

Being CSS code, double quotes should be used as much as possible, avoiding the use of single quotes. For example:

```css
.rule-name {
    content: "\00a7";
}
```


##### 4. Placeholders.

Inheritance and superclasses:

A class should not extend more than one placeholder.

```scss
.class-name {
    @extend %placeholder-name;

    ..
}
```


##### 5. Extensions.

Class extensions have a complexity of sharing and we don't normally use them the way you are really working.

Therefore, in principle we will try not to use the extensions to classes.


###### &#8594; _Code is poetry_