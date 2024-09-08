caching the results of expensive function calls and returning them when the same inputs are used again
is a technique for speeding up applications

Normal Function

```js
function fib(n) {
    if (n <= 1) {
        n
    }

    return fib(n - 1) + fib(n - 2)
}
```

Cached

```js
function fib(n, memo) {
    memo = memo || {}

    if (memo[n]) {
        return memo[n]
    }

    if (n <= 1) return n

    return memo[n] = fib(n - 1, memo) + fib(n - 2, memo)
}
```

more ex

```js
// Define a function to memoize
function multiply(x, y) {
    return x * y;
}

// Define a memoization cache as an object
const cache = {};

// Define a memoized version of the function
function memoizedMultiply(x, y) {
    const cacheKey = x + ":" + y;
    if (cache[cacheKey] !== undefined) {
        console.log('from cache')
        return cache[cacheKey];
    } else {
        const result = multiply(x, y);
        cache[cacheKey] = result;
        return result;
    }
}

// Call the memoized function
console.log(memoizedMultiply(2, 3)); // Should print "6"
console.log(memoizedMultiply(2, 3)); // Should print "6" again (result is already memoized)
```
