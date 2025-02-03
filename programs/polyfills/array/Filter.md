Array

```js
const myArr = [1, 2, 3, 4]
```

Usage

```js
const newArr = myArr.filter(el => el > 2)
console.log(newArr)
```

Solution

```js
Array.prototype.myFilter = function (callback) {
    const res = [];
    for (let i = 0; i < this.length; i++) {
        if (callback(this[i])) {
            res.push(this[i])
        }
    }
    return res
}

const newArr2 = myArr.myFilter(el => el > 2)
console.log(newArr2)
```