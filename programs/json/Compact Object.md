Create a function compactObject that takes an object or array as input and returns a new object or array with all falsy values removed, including in nested objects and arrays.

```javascript
function compactObject(obj) {
    if (obj === null || typeof obj !== 'object') {
        return obj;
    }

    if (Array.isArray(obj)) {
        return obj.filter(Boolean).map(compactObject);
    }

    const result = {};
    for (const key in obj) {
        const value = compactObject(obj[key]);
        if (Boolean(value)) {
            result[key] = value;
        }
    }
    return result;
}
```

Usage

```javascript
console.log(compactObject([null, 0, false, 1])); // [1]
console.log(compactObject({"a": null, "b": [false, 1]})); // {"b": [1]}
console.log(compactObject([null, 0, 5, [0], [false, 16]])); // [5, [], [16]]
```