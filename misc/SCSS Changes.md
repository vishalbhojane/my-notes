1. Binary operators (- and +):

```scss
// Before
$size: 10px;
div {
  margin: 15px -$size;
}

// After
$size: 10px;
div {
  margin: 15px - $size;
  // or
  margin: 15px (-$size);
}

// Compiled CSS (same for both)
div {
  margin: 5px;
}

// Benefit: Removes ambiguity, making it clear whether the - is intended
// as a binary operator or part of a negative value.
```

2. Division operator:

```scss
// Before
.item {
  width: (100px / 2);
}

// After
@use "sass:math";

.item {
  width: math.div(100px, 2);
}

// Compiled CSS (same for both)
.item {
  width: 50px;
}

// Benefit: Clearly distinguishes between division operations and CSS's
// use of / as a separator, improving compatibility with new CSS features.
```

3. Color functions with incorrect units:

```scss
// Before
$color: hsl(0.5turn, 100, 50);
.element {
  color: $color;
}

// After
$color: hsl(180deg, 100%, 50%);
.element {
  color: $color;
}

// Compiled CSS (same for both, but 'Before' version may produce incorrect color)
.element {
  color: #00ffff;
}

// Benefit: Ensures correct interpretation of color values, aligning
// with CSS specifications and preventing unexpected color outputs.
```

4. color.mix() with unitless weight:

```scss
// Before
$mixed: color.mix(red, blue, 50);
.element {
  background-color: $mixed;
}

// After
$mixed: color.mix(red, blue, 50%);
.element {
  background-color: $mixed;
}

// Compiled CSS (same for both)
.element {
  background-color: #800080;
}

// Benefit: Explicitly requires percentage units for weight, 
// reducing potential errors and aligning with the conceptual meaning of the parameter.
```

5. Extending compound selectors:

```scss
// Before
.message { border: 1px solid black; }
.info { font-size: 1.5rem; }
.heads-up {
  @extend .message.info;
}

// After
.message { border: 1px solid black; }
.info { font-size: 1.5rem; }
.heads-up {
  @extend .message, .info;
}

// Compiled CSS (Before - in LibSass, which is deprecated)
.message.info, .heads-up {
  border: 1px solid black;
  font-size: 1.5rem;
}

// Compiled CSS (After - in modern Sass implementations)
.message, .heads-up {
  border: 1px solid black;
}
.info, .heads-up {
  font-size: 1.5rem;
}

// Benefit: Provides more predictable and intuitive behavior for extends,
// ensuring that each class is extended separately as intended.
```

6. Custom Property Declarations:

```scss
// Before
$accent-color: #fbbc04;
:root {
  --accent-color: $accent-color;
}

// After
$accent-color: #fbbc04;
:root {
  --accent-color: #{$accent-color};
}

// Compiled CSS (same for both)
:root {
  --accent-color: #fbbc04;
}

// Benefit: Improves compatibility with CSS spec and allows for more 
// complex custom property values that might not be valid SassScript.
```

7. Variable Flags:

```scss
// Before
$var: value !default !default;

// After
$var: value !default;

// Benefit: Ensures consistency and removes redundant flags, 
// making the code cleaner and less prone to confusion.
```

8. ECMAScript Module Import:

```javascript
// Before
import sass from 'sass';

// After
import * as sass from 'sass';

// Benefit: Aligns with proper ESM syntax and type declarations, 
// ensuring better compatibility and type checking.
```

9. SassColor Constructor:

```javascript
// Before
new sass.SassColor({red: 102, green: 51, blue: 153, alpha: null});

// After
new sass.SassColor({red: 102, green: 51, blue: 153, alpha: 1});

// Benefit: Prepares for future support of CSS Color Module Level 4, 
// allowing for explicit distinction between opaque and missing alpha values.
```

10. abs() Function with Percentages:

```scss
// Before
$value: abs(10%);

// After
@use "sass:math";
$value: math.abs(10%);

// Benefit: Aligns with CSS spec behavior for abs() function, 
// preventing unexpected results when working with percentages.
```

11. Function and Mixin Names:

```scss
// Before
@function --my-function() { /* ... */ }

// After
@function my-function() { /* ... */ }

// Benefit: Prepares for potential future CSS support of native functions 
// and mixins, ensuring Sass can distinguish between its own and CSS declarations.
```

12. Nested Rules and Declarations Order:

```scss
// Before
.example {
  color: red;
  a { font-weight: bold; }
  font-weight: normal;
}

// After
.example {
  color: red;
  a { font-weight: bold; }
  & { font-weight: normal; }
}

// Benefit: Matches the new CSS nesting behavior, ensuring consistent 
// output between Sass and native CSS nesting.
```

13. meta.feature-exists() Function:

```scss
// Before
@if meta.feature-exists('custom-properties') {
  // Use custom properties
}

// After
// Remove the check entirely, or use alternative detection methods

// Benefit: Simplifies code by removing unnecessary feature checks, 
// as all modern Sass versions support these features.
```

14. Color Functions Deprecation:

```scss
// Before
@debug color.red(#c71585);
@debug saturate(#c71585, 20%);

// After
@use "sass:color";
@debug color.channel(#c71585, "red", $space: rgb);
@debug color.adjust(#c71585, $saturation: 20%, $space: hsl);

// Benefit: Provides unambiguous color manipulation across different color spaces,
// ensuring consistent results when working with modern CSS color features.
```

15. JS Color API Updates:

```javascript
// Before
const color = new sass.SassColor({red: 0x66, green: 0x33, blue: 0x99});
color.change({hue: 270});

// After
const color = new sass.SassColor({red: 0x66, green: 0x33, blue: 0x99});
color.change({hue: 270, space: "okclh"});

// Benefit: Explicitly specifies the color space for transformations,
// preventing ambiguity and unexpected results when working with different color spaces.
```

16. Legacy JS API Deprecation:

```javascript
// Before (Legacy API)
sass.render({
  file: 'input.scss',
  importer: function(url, prev, done) {
    // Importer logic
  },
  functions: {
    'custom-function($arg)': function(arg) {
      // Custom function logic
    }
  }
}, function(err, result) {
  // Callback logic
});

// After (Modern API)
sass.compile('input.scss', {
  importers: [{
    canonicalize(url) {
      // Canonicalization logic
    },
    load(canonicalUrl) {
      // Load logic
    }
  }],
  functions: {
    'custom-function($arg)': (args) => {
      // Custom function logic using modern Value class
    }
  }
}).then(result => {
  // Promise resolution logic
});

// Benefit: Provides a more modern, Promise-based API with better support for
// asynchronous operations, improved type safety, and more robust value handling.
```

17. Bundler Configuration (example for Vite):

```javascript
// Before (Vite 4)
// No configuration needed, uses legacy API by default

// After (Vite 5.4+)
// vite.config.js
export default {
  css: {
    preprocessorOptions: {
      scss: {
        api: "modern"
      }
    }
  }
}

// Benefit: Enables use of the modern Sass API in build tools,
// providing access to new features and improved performance.
```