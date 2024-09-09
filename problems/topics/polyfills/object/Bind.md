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
function printAge(age, year) {
    console.log(this.name + " is " + age + " years old, born in " + year)
}
```

Usage

```js
const vishalAge = printAge.bind(person1, 28);
vishalAge(1996);
```

Solution

```js
Function.prototype.mybind = function(obj, ...args1){

    if(typeof this != 'function'){
        throw new Error('Not callable')
    }

    obj.fn = this;
    return function(...args2){
        obj.fn(...args1, ...args2)
    }
}

const ankeshAge = printAge.mybind(person2, 24)
ankeshAge(2000)
```

