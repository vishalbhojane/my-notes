Array

```js
const arr = [1,2,[3,[4,5],6],7,[8]]
```

Usage

```js
console.log(arr.flat()) // default is 1, if not passed
```

Solution

```js
Array.prototype.myflat = function(depth = 1){

    if(!Array.isArray(this)){
        throw new Error(this + '.flat is not a function')
    }

    let result = [];

    for(let i = 0; i < this.length; i++){
        if(Array.isArray(this[i]) && depth > 0){
            result.push(...this[i].myflat(depth - 1))
        } else {
            result.push(this[i])
        }
    }

    return result
}

console.log(arr.myflat()) // default is 1, if not passed
```