Caching the results of expensive function calls and returning them when the same inputs are used again
Technique for speeding up applications

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

### Memoize Function

```js
function memoize(fn) {
    const cache = {}

    return function (...args) {
        const key = JSON.stringify(arguments)
        if (cache.hasOwnProperty(key)) {
            return cache[key]
        }
        return cache[key] = fn(...args)
    }
}
```

Usage

```js
function fib(n){
    if (n < 2) {
        return n
    }
    return fib(n - 1) + fib(n - 2)
}

const memoizedFib = memoize(fib)

console.log(memoizedFib(15))
console.log(memoizedFib(15))
```