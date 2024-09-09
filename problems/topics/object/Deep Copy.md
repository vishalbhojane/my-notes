```js
function deepCopy(val){
    if(['string', 'number', 'boolean'].includes(typeof val)){
        return val
    } else if(Array.isArray(val)){
        // return val.map(el => deepCopy(el))
        const arr = [];
        for(let i = 0; i < val.length; i++){
            arr.push(deepCopy(val[i]))
        }
        return arr
    } else {
        // return Object.keys(val).reduce((acc, curr) => acc[key] = deepCopy(val[key], {}))
        const obj = {};
        for(const key in val){
            obj[key] = deepCopy(val[key])
        }
        return obj
    }
}
```

Usage

```js
const arr = [1,2,[3,[4,5],6],7,[8]]

const arr2 = deepCopy(arr);
arr2.push('t')
console.log(arr2, arr);
```

```js
const obj = {
    name:'str',
    id:1,
    nest:{
        one:'one',
        two:'two'
    }
}

const obj2 = deepCopy(obj);
obj2.test = 't'
console.log(obj2, obj);
```