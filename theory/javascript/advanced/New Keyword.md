The `new` keyword in JavaScript is used to create new object instances from either
- Constructor function
- Class

The `new` keyword does the following to create an object:
1. Creates a new object instance.
2. Binds the new object's prototype to the parent's prototype property, i.e., a constructor function or a class.
3. Executes the function or the class with the given arguments, then binds the `this` keyword to the newly created object.
4. Returns the new object.

---
### Creating objects using the `new` keyword

From Constructor function

```js
function Writer(fname, lname) {
    //Properties
    this.firstName = fname;
    this.lastName = lname;

    //Method(S)
    this.sayName = () => {
        let fullName = `${this.firstName} ${this.lastName}`;

        console.log(fullName);
    }
}

let jsWriter = new Writer('Akande', 'Olalekan Toheeb');

console.log(jsWriter);
jsWriter.sayName();
```

From class

```js
class Writer {
    constructor(fname, lname) {
        //Properties
        this.firstName = fname,
            this.lastName = lname
    }

    //Method(s)
    sayName = () => {
        let fullName = `${this.firstName} ${this.lastName}`;

        console.log(fullName);
    }
}

let jsWriter = new Writer('Akande', 'Olalekan Toheeb');

console.log(jsWriter);
jsWriter.sayName();
```

Creating date from built-in Date constructor

```js
const date = new Date()
console.log(date, date.getDate(), date.getDay());
```

---
### The new keyword is a syntactic sugar for the call method on a function

```js
let jsWriter = Writer.call({}, 'Akande', 'Olalekan Toheeb')

console.log(jsWriter);
jsWriter.sayName();
```
