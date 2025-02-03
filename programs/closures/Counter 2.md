Problem Statement:
Create a function that takes an initial integer 'init' and returns an object with three methods:
1. increment(): Increases the current value by 1 and returns it.
2. decrement(): Decreases the current value by 1 and returns it.
3. reset(): Sets the current value back to 'init' and returns it.

## Solution

```javascript
var createCounter = function(init) {
    let count = init;

    return {
        increment() {
            return ++count;
        },
        decrement() {
            return --count;
        },
        reset() {
            count = init;
            return count;
        }
    };
};
```

Usage

```javascript
const counter = createCounter(0);
counter.increment(); // 1
counter.increment(); // 2
counter.decrement(); // 1
counter.reset(); // 0
counter.reset(); // 0
```