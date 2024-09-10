A power of two is a number of the form 2^n where n is an integer

```
1 = 2^0
2 = 2^1
3 !=
4 = 2^2
```

```
If number is less than two return false

while number is greator than one
	if number % 2 is !== 0, return false
	divide number by two
```

```js
function isPowerOfTwo(n){
    if(n < 1){ // number should be greater than 1
        return false
    }

    while(n > 1){
        if(n % 2 !== 0){
            return false
        }
        n = n / 2
    }   
    return true
}

console.log(isPowerOfTwo(4))
```

Time Complexity
O(log n)
## Optimized Approach

In binary a number that is, power of two, except for 1, ends with zero
`2 = 10`
`4 = 100`
`8 = 1000`

bitwise `AND` of this number with number less by 1, gives 0
`2 & 3`
`10 & 01 = 00`

`4 & 3`
`100 & 011 = 000`

`8 & 7`
`1000 & 0111 = 000`

```js
function isPowerOfTwo(n){
    if(n < 1){ // number should be greater than 1
        return false
    }
    return (n & (n-1)) === 0
}
```

Time Complexity
O(1)