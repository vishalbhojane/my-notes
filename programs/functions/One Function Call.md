Create a function once that takes a function fn as input and returns a new function. The new function should behave identically to fn, but ensure that fn is called at most once. Subsequent calls should return undefined.

```javascript
function once(fn) {
    let called = false;
    let result;

    return function(...args) {
        if (!called) {
            called = true;
            result = fn(...args);
            return result;
        }
    };
}
```

Usage

```javascript
const fn = (a, b, c) => a + b + c;
const onceFn = once(fn);

console.log(onceFn(1, 2, 3)); // 6
console.log(onceFn(2, 3, 6)); // undefined
console.log(onceFn(4, 5, 6)); // undefined
```