```js
/**
 * @param {number} number
 * @return {boolean}
 */
export default function isEven(number) {
  return (number & 1) === 0;
}

```

Decimal numbers are ends with zero in binary 
so doing AND with one will always results in zero

2 = 10
4 = 100