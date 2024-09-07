Array

```js
const myArr = [1, 2, 3, 4]
```

Usage

```js
myArr.forEach(function (el, i, arr) {
    arr[i] = el * 2;
})
console.log(myArr)
```

Solution

```js
Array.prototype.myforEach = function (callback) {
    for (let i = 0; i < this.length; i++) {
        callback(this[i], i, this)
    }
}

myArr.myforEach(function (el, i, arr) {
    arr[i] = el * 2
})
console.log(myArr)
```