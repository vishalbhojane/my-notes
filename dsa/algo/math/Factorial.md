The product of an integer and all the integers below it
`5! = 5 * 4 * 3 * 2 * 1 = 120`

```js
function factorial(n){
    let result = 1;

    for(let i = 2; i <= n; i++){
        result *= i
    }

    return result
}

console.log(factorial(5))
```

Time Complexity
O(n)

## Using Recursion

```js
function factorial(n){
    if(n === 0) {
        return 1
    }

    return n * factorial(n - 1)
}
```

Time Complexity
O(n^2 )

```js
console.log(factorial(5))

// logic
// n! = n * (n - 1)!
// 5! = 5 * 4!
// 5! = 5 * 4 * 3!
// 5! = 5 * 4 * 3 * 2!
// 5! = 5 * 4 * 3 * 2 * 1!
// 5! = 5 * 4 * 3 * 2 * 1 * 0!
// 5! = 5 * 4 * 3 * 2 * 1 * 1
```


