```js
function fibonacci(n){
    if(n < 2) {
        return n
    }
    return fibonacci(n-1) + fibonacci(n-2)
}
```

Time Complexity 
O(2^n)

```
// Fn = Fn-1 + Fn - 2
// F2 = F1 + F0
// F2 = 1 + 0
```