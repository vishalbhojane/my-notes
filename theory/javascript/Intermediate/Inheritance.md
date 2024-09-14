Inheritance refers to the mechanism that allows objects to acquire properties and methods from parent objects without redundant definition

### Prototypal inheritance

every object has an internal reference called prototype, pointing to another object that provides common properties and methods.

When accessing a property or method, the search starts at the object itself;
then, if the property isn't found, the search continues up the chain,
stopping at the prototype of `Object.prototype`

#### Array

```js
let arr = [1, 2, 3, 4, 5]
arr.__proto__ === Array.prototype
arr.__proto__.__proto__ === Object.prototype
arr.__proto__.__proto__.__proto__ === null
```
#### Object

```js
let object = {
    name: 'vishal',
    city: 'mumbai',
    getIntro: function () { console.log(this.name + " from " + this.city)}
}
object.__proto__ === Object.prototype
```
### Function

```js
function printHello() {
    console.log('hello');
}
printHello.__proto__ === Function.prototype
printHello.__proto__.__proto__ === Object.prototype
```

*Everything in JavaScript is an object*

---
### Changing the prototype (Never do this) ⚠

```js
let object2 = {
    name: 'ankesh',
}

object2.__proto__ = object
console.log(object2.name);  // > ankesh
console.log(object2.city);  // > mumbai (when we try to access the property or method it will first try to check in its context, then check in prototye)
object2.getIntro()
```
### Adding new properties and methods

```js
// creating custom polyfill for bind() method
Function.prototype.myBind = function () {
    // logic
}
```