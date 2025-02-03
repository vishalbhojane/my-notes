Create an asynchronous function sleep that takes a positive integer `millis` as input and returns a promise that resolves after `millis` milliseconds.

```javascript
async function sleep(millis) {
    return new Promise(resolve => setTimeout(resolve, millis));
}
```

Usage

```javascript
let t = Date.now();
sleep(100).then(() => {
    console.log(Date.now() - t); // Approximately 100
});
```