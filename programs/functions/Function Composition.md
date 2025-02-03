Create a function compose that takes an array of functions and returns a new function that is the composition of those functions. The composition should be applied from right to left.

```javascript
function compose(functions) {
    return function(x) {
        return functions.reduceRight((acc, fn) => fn(acc), x);
    }
}
```

Usage

```javascript
const fn1 = compose([x => x + 1, x => x * x, x => 2 * x]);
console.log(fn1(4)); // 65

const fn2 = compose([x => 10 * x, x => 10 * x, x => 10 * x]);
console.log(fn2(1)); // 1000

const fn3 = compose([]);
console.log(fn3(42)); // 42
```