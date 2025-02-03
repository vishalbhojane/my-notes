```javascript
function isObject(obj) {
    return (obj !== null && typeof obj === 'object');
}

function compareObject(obj1, obj2) {
    const keysArr1 = Object.keys(obj1);
    const keysArr2 = Object.keys(obj2);

    if (keysArr1.length !== keysArr2.length) return false;

    for (let key of keysArr1) {
        if (!obj2.hasOwnProperty(key)) return false;

        const value1 = obj1[key];
        const value2 = obj2[key];

        const areObjects = isObject(value1) && isObject(value2);

        if (areObjects && !compareObject(value1, value2)) {
            return false;
        }

        if (!areObjects && value1 !== value2) {
            return false;
        }
    }

    return true;
}
```

Usage

```javascript
const obj3 = {
    name: 'vishal',
    id: 0,
    address: {
        city: 'New York',
        zip: '10001'
    }
};

const obj4 = {
    name: 'vishal',
    id: 0,
    address: {
        city: 'New York',
        zip: '10001'
    }
};

const obj5 = {
    id: 0,
    name: 'vishal'
};

console.log(compareObject(obj3, obj4)); // Should print true
console.log(compareObject(obj1, obj5)); // Should print true
console.log(compareObject(obj1, obj3)); // Should print false
```
