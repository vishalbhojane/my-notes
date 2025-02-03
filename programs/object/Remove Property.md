Solution

```js
function stripProperty(obj, property) {

    if (obj.hasOwnProperty(property)) {
        delete obj[property]
    }

    return obj
}
```

Usage

```javascript
const person = {
    name: 'vishal',
    giveUp: 'false'
};

console.log(person);  // { name: 'vishal', giveUp: 'false' }
stripProperty(person, 'giveUp');
console.log(person);  // { name: 'vishal' }
```
