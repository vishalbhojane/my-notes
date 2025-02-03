Problem Statement:
Create a function cancellable that takes a function fn, an array of arguments args, and a timeout t in milliseconds. It should:
1. Schedule fn to be called with args after t milliseconds.
2. Return a cancel function that, when called, prevents fn from being executed if it hasn't been called yet.

```javascript
function cancellable(fn, args, t) {
    const timer = setTimeout(() => fn(...args), t);
    
    return function cancelFn() {
        clearTimeout(timer);
    };
}
```

Usage

```javascript
const fn = (x) => x * 5;
const args = [2];
const t = 20;
const cancelTimeMs = 50;

const cancel = cancellable(fn, args, t);
setTimeout(cancel, cancelTimeMs);
```
