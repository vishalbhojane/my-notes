Create a function that takes an integer n and returns a counter function. The counter function should:
1. Initially return n
2. Return 1 more than the previous value on subsequent calls

## Solution

```javascript
var createCounter = function(n) {
    let num = n;
    return function() {
        return num++;
    };
};
```

Usage

```javascript
const counter = createCounter(-2);
counter(); // -2
counter(); // -1
counter(); // 0
counter(); // 1
counter(); // 2
```
