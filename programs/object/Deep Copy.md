```javascript
function deepCopy(val) {
    // Handle primitive types
    if (['string', 'number', 'boolean'].includes(typeof val)) {
        return val;
    } 
    // Handle arrays
    else if (Array.isArray(val)) {
        const arr = [];
        for (let i = 0; i < val.length; i++) {
            arr.push(deepCopy(val[i]));
        }
        return arr;
    } 
    // Handle objects
    else {
        const obj = {};
        for (const key in val) {
            obj[key] = deepCopy(val[key]);
        }
        return obj;
    }
}
```

Usage

```javascript
// Array example
const arr = [1, 2, [3, [4, 5], 6], 7, [8]];
const arr2 = deepCopy(arr);
arr2.push('t');
console.log(arr2, arr);

// Object example
const obj = {
    name: 'str',
    id: 1,
    nest: {
        one: 'one',
        two: 'two'
    }
};
const obj2 = deepCopy(obj);
obj2.test = 't';
console.log(obj2, obj);
```