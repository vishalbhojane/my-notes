A number that can be divided exactly only by itself and 1
For example `7, 17 and 41 1`

```js
function isPrime(n){
    if(n < 2) {
        return false
    }

    for(let i = 2; i < n; i++){ // Optimized, i <= Math.sqrt(n), O(log n)
        if((n % i) === 0){
            return false
        }
    }

    return true
}

console.log(isPrime(7))
```

Time complexity
O(n)

### Optimized way
Integers larger than the square root do not need to be checked
`n = a * b`, one of the two factors 'a' and 'b' is less than or equal to square root of 'n'