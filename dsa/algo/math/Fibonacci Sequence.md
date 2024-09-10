A series of numbers in which each number ( Fibonacci number ) is the sum of the two preceding numbers.
The simplest is the series 0, 1, 1, 2, 3

```js
function fibonacci(n) {
    const sequence = [0, 1];

    for (let i = 2; i < n; i++) {
        sequence[i] = sequence[i - 1] + sequence[i - 2]
    }

    return sequence
}

console.log(fibonacci(5))
```

Time Complexity
O(n)

