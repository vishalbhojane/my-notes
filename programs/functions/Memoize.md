Create a memoize function that takes a function as input and returns a memoized version of that function. The memoized function should cache results for unique input combinations and return cached results for repeated calls with the same inputs.

```javascript
function memoize(fn) {
    const cache = new Map();
    
    return function(...args) {
        const key = JSON.stringify(args);
        
        if (cache.has(key)) {
            return cache.get(key);
        }
        
        const result = fn(...args);
        cache.set(key, result);
        return result;
    }
}
```

Usage

```javascript
const sum = (a, b) => a + b;
const memoizedSum = memoize(sum);

console.log(memoizedSum(2, 3)); // 5 (calculated)
console.log(memoizedSum(2, 3)); // 5 (from cache)
console.log(memoizedSum(3, 2)); // 5 (calculated, different order)
```
