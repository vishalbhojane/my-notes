Create a function that takes two promises which resolve to numbers, and returns a new promise that resolves to the sum of these numbers.

```javascript
var addTwoPromises = async function(promise1, promise2) {
    const [value1, value2] = await Promise.all([promise1, promise2]);
    return value1 + value2;
};
```

Usage

```javascript
const promise1 = new Promise(resolve => setTimeout(() => resolve(10), 50));
const promise2 = new Promise(resolve => setTimeout(() => resolve(-12), 30));
addTwoPromises(promise1, promise2).then(console.log); // -2
```
