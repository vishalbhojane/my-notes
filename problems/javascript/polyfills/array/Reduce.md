Array

```js
const myArr = [1, 2, 3, 4]
```

Usage

```js
const newArr = myArr.reduce((acc, curr) => acc + curr)
console.log(newArr)
```

Solution

```js
Array.prototype.myreduce = function (callback, initialValue) {
    let acc = initialValue;

    for (let i = 0; i < this.length; i++) {
        acc = acc !== undefined ? callback(acc,this[i]) : this[i]
    }

    return acc
}

const newArr2 = myArr.myreduce((acc, curr) => acc + curr)
console.log(newArr2)
```