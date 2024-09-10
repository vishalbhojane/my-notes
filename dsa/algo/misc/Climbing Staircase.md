There are n stairs, a person standing at the bottom wants to climb stairs to reach the nth stair.
The person can climb either 1 stair or 2 stairs at a time
the task is to count the number of ways that a person can reach at the top

Input: `n = 1`
Output: 1
Explanation : There is only one way to climb 1 stair

Input: `n = 2`
Output: 2
Explanation : There are two ways: `(1, 1) and (2)`

Input: `n = 4`
Output: 5
Explanation : `(1, 1, 1, 1), (1, 1, 2), (2, 1, 1), (1, 2, 1), (2, 2)`

**Tip**
here we can observe Fibonacci pattern
`climbingStaricase(n) = climbingStaricase(n - 1) + climbingStaricase(n - 2)`

1 = 1

n = 2
`climbingStaricase(2 - 1)` + `climbingStaricase(2 - 2)` = 2
`1` + `0`
1

n = 3
`climbingStaricase(3 - 1)` + `climbingStaricase(3 - 2)`
`climbingStaricase(2)` + `climbingStaricase(1)`
`2` + `1`
3

n = 4
`climbingStaricase(3)` + ``climbingStaricase(2)`
3 + 2
5

```js
function climbingStaricase(n) {
    const numOfWays = [1, 2]

    for(let i = 2; i <= n; i++){
        numOfWays[i] = numOfWays[i - 1] + numOfWays[i - 2]
    }

    return numOfWays[n - 1]
}

console.log(climbingStaricase(1))
console.log(climbingStaricase(2))
console.log(climbingStaricase(3))
console.log(climbingStaricase(4))
```

Time Complexity
O(n)

