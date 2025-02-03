Create a function `cancellable` that takes a function `fn`, an array of arguments `args`, and an interval `t`. It should:
1. Immediately call `fn` with `args`.
2. Call `fn` with `args` every `t` milliseconds.
3. Return a cancel function that stops the repeated calls when invoked.

```javascript
function cancellable(fn, args, t) {
    fn(...args);
    const timer = setInterval(() => fn(...args), t);
    
    return function cancelFn() {
        clearInterval(timer);
    };
}
```

Usage

```javascript
const fn = (x) => x * 2;
const args = [4];
const t = 35;
const cancelTimeMs = 190;

const cancel = cancellable(fn, args, t);
setTimeout(cancel, cancelTimeMs);
```