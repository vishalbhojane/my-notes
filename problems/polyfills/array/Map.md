Array

```js
const myArr = [1, 2, 3, 4]
```

Usage

```js
const newArr = myArr.map(el => el * 2)
console.log(newArr)
```

Solution

```js
Array.prototype.mymap = function (callback) {
    const res = [];
    for (let i = 0; i < this.length; i++) {
            res.push(callback(this[i], i, this))
    }
    return res
}

const newArr2 = myArr.mymap(el => el * 2)
console.log(newArr2)
```

`map` method also takes second argument, `thisArg`
`map(callback, thisArg)`

```js
res.push(callback.call(thisArg ,this[i], i, this))
```

Edge case
only push to array when item is not undefined

```js
if(this[i] !== undefined){
    res.push(callback(this[i], i, this))
}
```