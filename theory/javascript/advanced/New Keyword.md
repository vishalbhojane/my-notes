The `new` keyword is use create an instance of a user-defined object type or of one of the built-in object types that has a constructor function.

Creating date from built-in object

```js
const date = new Date()
console.log(date, date.getDate(), date.getDay());
```

Constructor function

```js
function Fruit(color, taste, seeds) {
    this.color = color;
    this.taste = taste;
    this.seeds = seeds;
    // Note: we are not returning anything here, The compiler will implicitly insert ‘return this’ at the end.
}
 
// Create an object
const fruit1 = new Fruit('Yellow', 'Sweet', 1);
 
// Display the result
console.log(fruit1);
// Fruit {color: 'Yellow', taste: 'Sweet', seeds: 1}
```

More ex

```js
function func() {
    let c = 1;
    this.a = 100;
}
 
// Set the function prototype
func.prototype.b = 200;
 
// Create an object
let obj = new func();

obj.prototype.c = 300; //> Cannot set properties of undefined (setting 'c')
 
// Display the result on console
console.log(obj); //> func { a: 100 }
console.log(obj.a); //> 100
console.log(obj.b); //> 200
```

Using class

```js
class User {
    constructor(name, age) {
        this.name = name
        this.age = age
    }
    //adding function to class
    printName() {
        console.log(this.name)
    }
}

const userClass = new User("Ankesh", 23)
const userClass2 = new User("Veena", 25)

userClass.printName()
userClass2.printName()
```