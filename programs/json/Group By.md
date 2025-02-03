Extend the Array prototype to include a groupBy method that takes a callback function fn as an argument. The method should return an object where each key is the result of fn(item) for each item in the array, and each value is an array of all items that produced that key.

```js
Array.prototype.groupBy = function(fn) {
    const result = {}

    this.forEach(item => {
        const key = fn(item)

        if(!result[key]){
           result[key] = [] 
        }
        result[key].push(item)
    })
    return result
};
```

Usage

```javascript
console.log([{id:"1"}, {id:"1"}, {id:"2"}].groupBy(item => item.id));
// { "1": [{id:"1"}, {id:"1"}], "2": [{id:"2"}] }

console.log([[1,2,3], [1,3,5], [1,5,9]].groupBy(list => String(list[0])));
// { "1": [[1,2,3], [1,3,5], [1,5,9]] }

console.log([1,2,3,4,5,6,7,8,9,10].groupBy(n => String(n > 5)));
// { "true": [6,7,8,9,10], "false": [1,2,3,4,5] }
```
