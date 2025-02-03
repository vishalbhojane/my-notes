Implement a function `promiseAll` that takes an array of asynchronous functions and returns a promise that:
1. Resolves with an array of all resolved values when all promises are fulfilled.
2. Rejects with the reason of the first rejection if any promise is rejected.
3. Executes all promises in parallel.

```javascript
function promiseAll(functions) {
    return new Promise((resolve, reject) => {
        const results = new Array(functions.length);
        let resolvedCount = 0;

        functions.forEach((fn, index) => {
            fn().then(
                value => {
                    results[index] = value;
                    if (++resolvedCount === functions.length) {
                        resolve(results);
                    }
                },
                reject
            );
        });
    });
}
```