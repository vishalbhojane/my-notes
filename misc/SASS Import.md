## Basic Import:

Before

```scss
@import 'variables';
@import 'mixins';

body {
  background-color: $primary-color;
  @include border-radius(5px);
}
```

After

```scss
@use 'variables';
@use 'mixins';

body {
  background-color: variables.$primary-color;
  @include mixins.border-radius(5px);
}
```

## Importing with Namespace

Before

```scss
@import 'utils/colors';
@import 'utils/functions';

.element {
  color: $primary-color;
  width: calculate-width(100%);
}
```

After

```scss
@use 'utils/colors' as c;
@use 'utils/functions' as f;

.element {
  color: c.$primary-color;
  width: f.calculate-width(100%);
}
```

## Importing Multiple Files

Before

```scss
@import 'reset', 'typography', 'layout';

body {
  @include container;
  font-family: $base-font;
}
```

After

```scss
@use 'reset';
@use 'typography' as t;
@use 'layout' as l;

body {
  @include l.container;
  font-family: t.$base-font;
}
```

## Importing with Default Namespace

Before

```scss
@import 'math';

.circle {
  width: pow(5, 2) * 1px;
}
```

After

```scss
@use 'sass:math';

.circle {
  width: math.pow(5, 2) * 1px;
}
```

## Importing and Overriding Variables:

```scss
// _variables.scss
$primary-color: blue;

// main.scss
@import 'variables';
$primary-color: red;

body {
  color: $primary-color; // red
}
```

After

```scss
// _variables.scss
$primary-color: blue !default;

// main.scss
@use 'variables' with (
  $primary-color: red
);

body {
  color: variables.$primary-color; // red
}
```

