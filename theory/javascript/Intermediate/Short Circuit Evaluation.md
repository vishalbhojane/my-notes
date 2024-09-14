In short-circuit evaluation, an expression with logical operators (`||` and `&&`) is evaluated from left to right.
So, if the condition is met and the rest of the conditions won’t affect the already evaluated result, the expression will short-circuit and return that result.

### Logical OR (`||`) Operator

This operator will return the first true value.
So, it won’t even reach the rest of the conditions and return true as the condition is satisfied.

```js
true || false
// true
```

### Logical AND(`&&`) Operator

This operator will return false as soon as it gets any falsy value and will return the last true value if all the values are truthy.

```js
false && true
// false
```

more ex

```js
function printTrue() {
    console.log("true")
    return true
}

function printFalse() {
    console.log("false")
    return false
}
```

OR - if anything is true => true

```js
printTrue() || printFalse() // here JS will only run printTrue() and won't run second.
printFalse() || printTrue() // here JS will run both, because it dont know what will be the end result
```

AND - if anything is false = false

```js
printFalse() && printTrue() // only printFalse() will run
printTrue() && printFalse() // both will run
```

---
### Use of short circuit evaluation

OR

```js
// normal way
function printName(name) {
    if (name == null) {
        name = "Default"
    }
    console.log(name)
}
printName("vishal") //> vishal
printName() //Default

// using short circuit evaluation
function printName(name) {
    name = name || "Default"
    console.log(name)
}
```

AND

```js
const person = {
    address: {
        street: "main street"
    }
}
// normal way
if (person != null && person.address != null) {
    console.log(person.address.street)
}

// using short circuit evaluation
console.log(person && person.address && person.address.street)
```