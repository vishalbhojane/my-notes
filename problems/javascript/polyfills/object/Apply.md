Objects

```js
const person1 = {
    name:'vishal'
}
const person2 = {
    name:'ankesh'
}
```

Function

```js
function printAge(age) {
    console.log(this.name + " is " + age + " years old")
}
```

Usage

```js
printAge.apply(person1, [28])
```

Solution

```js
Function.prototype.myapply = function(obj = {}, args){
    if(typeof this !== 'function'){
        throw new Error('no callable')
    }

    if(!Array.isArray(args)){
        throw new Error('TypeError: CreateListFromArrayLike called on non-object')
    }

    obj.fn = this;
    obj.fn(...args)
}

printAge.myapply(person2, [24])
```

