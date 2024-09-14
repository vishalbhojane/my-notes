Type coercion is the automatic or implicit conversion of values from one data type to another

### Explicit type coercion

Because we are explicitly saying we want to convert string to number

```js
let value1 = "1";
let value2 = "1.3";
let value3 = 3;
parseInt(value1);
parseFloat(value2);
value3.toString();
```

### Implicit type coercion

JS will convert number to strings when adding number and string

```js
let value4 = 1;
const value5 = "Hello ";
let value6 = "3";
console.log(value4 + value5) // here JS is doing type coercion => console.log(a.toString() + b); output will be "1hello "
console.log(value4 - value5) // will return NaN
console.log(value6 - value4) // will return 2
console.log(value6 + value4) // will return 31
```

Zero is consider as a false when loosely checking

```js
0 == false // js will return true
```

---

### Avoiding Type coercion when comparing two different types

ALWAYS USE `===` (three equal signs) when checking two types, `!==` to check not equal
but use  `==` (double equal) to check `undefined` and `null`

---
### `NaN`

```js
let a = 'asdfasd'
parseInt(a) //=> will return NaN
parseInt(a) == NaN //=> but this will return false
parseInt(a) === NaN //=> also this will return false
```

to check Nan

```js
let b = 'asd'
isNaN(b) //will return true
```

---
##### Questions

```js
console.log(3 > 2 > 1)
// true > 1
// 1 > 1
// false
```

```js
console.log(1 < 2 < 3);
// true < 3
// 1 < 3
// true
```