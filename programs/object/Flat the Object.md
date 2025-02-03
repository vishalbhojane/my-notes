Using `Array.reduce()`:

```javascript
const flattenObject = (obj, prefix = "") => {
    return Object.keys(obj).reduce((acc, key) => {
        const pre = prefix.length ? `${prefix}.` : '';
        if (
            obj[key] !== null &&
            typeof obj[key] === 'object' &&
            Object.keys(obj[key]).length > 0
        ) {
            Object.assign(acc, flattenObject(obj[key], pre + key));
        } else {
            acc[pre + key] = obj[key];
        }
        return acc;
    }, {});
}
```

Using `Array.forEach()`:

```javascript
function flattenObject2(obj, prefix = "") {
    let result = {};

    Object.keys(obj).forEach(function(key) {
        const pre = prefix.length ? `${prefix}.` : '';

        if (
            obj[key] !== null &&
            typeof obj[key] === 'object' &&
            Object.keys(obj[key]).length > 0
        ) {
            result = {...result, ...flattenObject2(obj[key], pre + key)};
        } else {
            result[pre + key] = obj[key];
        }
    });
    
    return result;
}
```

Usage

```javascript
const data = {
    'name': {
        'last': 'Sridhar',
        'first': {
            'des': 'Mr',
            'value': 'Preetham'
        }
    }
}

console.log(flattenObject(data));
// { 'name.last': 'Sridhar', 'name.first.des': 'Mr', 'name.first.value': 'Preetham' }
```