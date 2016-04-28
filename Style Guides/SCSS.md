# SCSS

A minimalist's guide to modular SCSS.



<br />
## Table of Contents

- [Structure](#structure)
- [Comments](#comments)
- [Selectors](#selectors)
- [Naming conventions](#naming conventions)
- [Variables](#variables)



<br />
## Structure

#### Spaces or tabs

Use **spaces** and indent **2 spaces** per indentation level.


#### Nesting

Don’t nest selectors. Instead, just indent to imply a nested DOM structure:

###### Bad

```scss
.modal {
  // ...
  .modal-content {
    // ...
  }
}
```

###### Good

```scss
.modal {
  // ...
}

  .modal-content {
    // ...
  }
```


#### Whitespace

Maintain 3 line breaks between blocks and 1 line break between a block’s “nested” elements:

###### Bad

```scss
.modal {
  // ...
}
  .modal-content {
    // ...
  }

.modal_opened {
  // ...
}
  .modal_opened .modal-content {
    // ...
  }
```

###### Good

```scss
.modal {
  // ...
}

  .modal-content {
    // ...
  }



.modal_opened {
  // ...
}

  .modal_opened .modal-content {
    // ...
  }
```

If a selector has lots of declarations, then group them and add a single line break for readability:

###### Bad

```scss
.modal {
  display         : flex;
  position        : absolute;
  top             : 0;
  transition      : $timing--modal ease-out;
  background      : $color-background--overlay;
  left            : 0;
  align-items     : center;
  right           : 0;
  justify-content : center;
  bottom          : 0;
}
```

###### Good

```scss
.modal {
  position        : absolute;
  top             : 0;
  left            : 0;
  right           : 0;
  bottom          : 0;

  background      : $color-background--overlay;

  display         : flex;
  justify-content : center;
  align-items     : center;

  transition      : $timing--modal ease-out;
}
```


#### Alignment

Align properties in a declaration:

###### Bad

```scss
.modal {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
```

###### Good

```scss
.modal {
  position : absolute;
  top      : 0;
  left     : 0;
  right    : 0;
  bottom   : 0;
}
```



<br />
## Comments

Comments are necessary to describe to humans what a snippet of code is doing - however, they must be as concise as possible to make them easier to maintain as the snippet evolves.


### Things to do

1. Keep the present tense
* Be concise
* Split long lines
* Use proper spelling, punctuation, and grammar
* **Always** document why a “magic” number is used


### Things to NOT do

1. Use pronouns (eg. we, I, you, etc.)
* Use unnecessary punctuation
  * Eg. `Round all the corners!!!1`



### Types


#### Inline

Inline comments should only be inside of a selector’s declaration wrapping curly braces.

##### When to use

* Non-trivial snippets (eg. “magic” numbers, layout hacks)
* Unintuitive logic (eg. workarounds)
* Line-specific annotations (eg. `// TODO: once base reset styles are fixed, remove this`)



They should always appear *before* the line they are describing:

###### Bad

```scss
.selector {
  margin-top: 1px; // Compensate for border
}
```

###### Good

```scss
.selector {
  // Compensate for border
  margin-top: 1px;
}
```


#### Block

Block comments should be made for any file to impose certain conventions or separate large blocks of code (eg. variable definition files).

```scss
/**
 * These variables are for color aliases only.
 * They ARE to be used in components.
 * If a variable doesn't exist for a use case,
 * alias the color definition from _colors-definitions.scss
 *
 * This is meant to define the colors used in general contexts.
 *
 * IMPORTANT:
 * DO be general.
 * DO NOT be specific.
 * $color-icon--white // good
 * $color-icon--duration // bad
 */



/**
 * Texts
 */

$color-text--black             : $black;
$color-text--blue              : $blue;
$color-text--white             : $white;
// ...



/**
 * Links
 */

$color-link--blue : $blue;
// ...
```



<br />
## Selectors

* Use classes (not ids)
* Use `data-ui` attributes for dynamic styles that aren't states, such as theme-ing


Example:

```scss
.profile {
  // ...
}



.profile[data-ui-theme=blue] {
  background: $color-background--blue;
}
```



<br />
## Naming conventions

Be descriptive with your naming choice. Avoid unnecessary abbreviations:

```scss
// Bad
.btn {}

// Good
.button {}
```

### BEM

To simplify our styles and avoid namespace collisions, we follow a variation of [the BEM pattern](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/).

In short, each class name is a composition of 3 parts:

1. the **B**lock,
* the **E**lement, and
* the **M**odifier.

The syntax we use is:

```scss
.blockName-elementName_modifierName {}
```


Example:

```scss
// The Block
.workoutCover {}

  // An Element
  .workoutCover-image {}

  // An Element
  .workoutCover-layoutRow {}

  // An Element-Modifier
  .workoutCover-layoutRow_top {}

  // An Element-Modifier
  .workoutCover-layoutRow_bottom {}



// A Block-Modifier
.workoutCover_full {}
```



<br />
## Variables

[TODO]

..variables & variable definitions











<br><br><br><br><br><br>
