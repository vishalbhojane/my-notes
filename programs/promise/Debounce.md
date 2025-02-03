Implement a debounce function that delays the execution of a given function by t milliseconds. If the debounced function is called again within this time window, the previous execution is cancelled and the timer resets. Solution:

```javascript
function debounce(fn, t) {
    let timeoutId;
    
    return function(...args) {
        clearTimeout(timeoutId);
        
        timeoutId = setTimeout(() => {
            fn.apply(this, args);
        }, t);
    };
}
```

Usage

```javascript
const debouncedLog = debounce(console.log, 100);
debouncedLog('Hello'); // Cancelled
debouncedLog('World'); // Logged after 100ms
```