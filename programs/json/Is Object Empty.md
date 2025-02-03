Create a function isEmpty that takes an object or an array as input and returns true if it's empty, false otherwise.

```javascript
function isEmpty(obj) {
    if (Array.isArray(obj)) {
        return obj.length === 0;
    } else if (typeof obj === 'object' && obj !== null) {
        return Object.keys(obj).length === 0;
    }
    return false;
}
```

Usage

```javascript
console.log(isEmpty({"x": 5, "y": 42})); // false
console.log(isEmpty({})); // true
console.log(isEmpty([null, false, 0])); // false
console.log(isEmpty([])); // true
console.log(isEmpty(null)); // false
```