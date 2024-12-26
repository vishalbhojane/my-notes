**Overlapping Subproblems** refers to a property of certain problems in which the same subproblems are solved multiple times during the computation of the overall solution.

In such cases, dynamic programming is used to store the results of these subproblems to avoid redundant calculations, thereby improving efficiency.

This characteristic is often found in problems involving recursive solutions where the same calculations can be reused.

eg. Fibonacci Sequence, Coin Change Problem

```js
// Fibonacci without memoization O(2^n)
let counter = 0;

function fib(n) {
  counter++;
  if (n === 0 || n === 1) {
    return n;
  }
  return fib(n - 1) + fib(n + 2);
}

// fib(7) = 13, counter = 41
// fib(20) = 6765, counter = 21891
// fib(40) = 102334155, counter = 331160281
```

```js
// Using memoization, O(2n - 1) === O(2n) === O(n)
let counter = 0;
let memo = [];

function fib(n) {
  counter++;
  if (memo[n] !== undefined) {
    return memo[n];
  }
  if (n === 0 || n === 1) {
    return n;
  }
  return (memo[n] = fib(n - 1) + fib(n - 2));
}

// fib(7) = 13, counter = 13
// fib(40) = 102334155, counter = 79
```

```js
// Bottom up approach = O(n - 1)

function fib(n){
  let fibArray = [0,1]

  for(let i = 2 ;i <=n; i++){
    fibArray[i] = fibArray[i - 1] + fibArray[i - 2];
  }
  return fibArray[n];
}

// fib(7) = 13, counter = 6
// fib(40) = 102334155, counter = 39
```