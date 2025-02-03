Create a function timeLimit that takes an asynchronous function fn and a time limit t in milliseconds. It should return a new function that:
1. Resolves with the result of fn if it completes within t milliseconds.
2. Rejects with "Time Limit Exceeded" if fn takes longer than t milliseconds.
3. Rejects with any error that fn might throw.

```javascript
function timeLimit(fn, t) {
    return async function(...args) {
        return Promise.race([
            fn(...args),
            new Promise((_, reject) => 
                setTimeout(() => reject("Time Limit Exceeded"), t)
            )
        ]);
    }
}
```