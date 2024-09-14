### Is Even

```js
/**
 * @param {number} number
 * @return {boolean}
 */
export default function isEven(number) {
  return (number & 1) === 0;
}
```
### Is Positive

JavaScript stores numbers as 64 bits floating point numbers, but all bitwise operations are performed on 32 bits binary numbers.
*Before a bitwise operation is performed, JavaScript converts numbers to 32 bits signed integers*

```js
/**
 * @param {number} number - 32-bit integer.
 * @return {boolean}
 */
export default function isPositive(number) {
  // Zero is neither a positive nor a negative number.
  if (number === 0) {
    return false;
  }

  // The most significant 32nd bit can be used to determine whether the number is positive.
  return ((number >> 31) & 1) === 0;
}
```
### Is Power of Two

```js
/**
 * @param {number} number
 * @return bool
 */
export default function isPowerOfTwo(number) {
  return (number & (number - 1)) === 0;
}
```
### Divide by Two

```js
/**
 * @param {number} number
 * @return {number}
 */
export default function divideByTwo(number) {
  return number >> 1;
}
```
### Multiply by Two

```js
/**
 * @param {number} number
 * @return {number}
 */
export default function multiplyByTwo(number) {
  return number << 1;
}
```
