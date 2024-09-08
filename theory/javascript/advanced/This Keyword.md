this keyword, dynamically refers to the object executing a function or method

Itself, this points to the global object. (Default binding)

```js
console.log(this, 'global scope')
// window (if ran on browser), global in nodejs
```

Within a function, this typically points to the global object.

```js
function x() {
    console.log(this, 'function scope');
}
x()
//window (if ran on browser), global in nodejs
```

In a function under strict mode, this becomes undefined.

```js
'use strict'
function x() {
    console.log(this, 'function scope');
}
x()
// undefined

window.x()
// window (if ran on browser)
```

inside arrow function refers to the enclosing lexical context

```js
const obj2 = {
    a: 10,
    x: () => { console.log(this, 'obj scope with arrow function')}
}
obj2.x(); // widow object because the 'obj2' has a global lexical context

const obj3 = {
    a: 10,
    x: function () {
        // enclosing lexical context
        const y = () => { console.log(this, 'obj scope')}
        y();
    }
}
obj3.x(); //> Returns obj3
```

Within a method of an object, this points to that object.

```js
const obj = {
    a: 10,
    x: function () { // function inside an object is known as a method
        console.log(this, 'obj scope');
    }
}
obj.x(); //> { a: 10, x: f} 'obj scope'
```

During an event, this points to the element that triggered the event.

```html
<button onclick="console.log(this)">Click Me</button>
```

Methods such as `call()`, `apply()`, and `bind()` can reassign this to any desired object.

```js
const student = {
    name: 'vishal',
    printName: function () {
        console.log(this.name);
    }
}
student.printName();

const student2 = {
    name: 'ankesh',
}
student.printName.call(student2) // value of 'this' can be modify using call method
```

## Part 2

`this` keyword refers to the object it belongs to
it makes function reusable by letting you decide the object value
this value is determined by entirely how the function is called

### implicit binding

```js
const person = {
    name:'vishal',
    sayMyName: function(){
        console.log('my name is ', this.name)
    }
}
person.sayMyName()
```

### explicit binding

```js
function sayMyName(){
    console.log('my name is ', this.name)
}
sayMyName.call(person)
```

### `new` binding

```js
function Person(name){ // constructor function
    // here constructor function returns an empty object {}
    this.name = name
}
const p1 = new Person('vishal')
// {name:'vishal'}
```

### default binding = refers to global object
```js
// name = 'vishal'
function sayMyName(){
    console.log('my name is ', this.name)
}
sayMyName()
// my name is undefined
// my name is vishal (if contains a global variable 'name')
```

### Order precedence

New Binding
Explicit binding
Implicit binding
Default binding

### Adding a method in Person (refer to prototype)

`prototypes` are used to share properties and methods across the instances
prototypal inheritance

```js
Person.prototype.sayMyName = sayMyName
```