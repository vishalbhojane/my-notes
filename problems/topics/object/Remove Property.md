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

```js
const person = {
    name: 'vishal',
    giveUp: 'true'
}

console.log(person)
stripProperty(person, 'giveUp')
console.log(person)
```
