Objects

```js
const obj1 = {
    name: 'vishal',
    id: 0
}

const obj2 = {
    name: 'vishal',
    id: 0
}
```

Helper Function

```js
function isObject(obj){
    return (obj !== null && typeof obj === 'object')
}
```

Solution

```js

function compareObject(obj1, obj2){
    const keysArr1 = Object.keys(obj1)
    const keysArr2 = Object.keys(obj2)

    if(keysArr1.length !== keysArr2.length) return false

    for (let key of keysArr1){
        const value1 = obj1[key];
        const value2 = obj2[key];

        const isobject = isObject(value1) && isObject(value2)

        if(!isobject && value1 !== value2) return false

        if(isobject && !compareObject(value1, value2)) return false

        return true
    }
}

console.log(compareObject(obj1, obj2))
```

Steps
get `keys` array for both
check `length`
compare values of both
if values are object (i.e nested object), recursion