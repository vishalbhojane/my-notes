Create a function that returns a new function. The returned function should always return the string "Hello World", regardless of any arguments passed to it.
## Solution

```javascript
var createHelloWorld = function() {
    return function(...args) {
        return "Hello World";
    }
}
```
