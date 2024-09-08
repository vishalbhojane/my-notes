*Classes are syntactical sugar over prototypal inheritance (ES6)*

#### before class

```js
function Person(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
}
Person.prototype.sayMyName = function () {
    console.log(this.firstName + " " + this.lastName);
}
```

inheriting from above Person

```js
function SuperHero(firstName, lastName) {
    // here `this` keyword creates empty {}
    Person.call(this, firstName, lastName)
    this.isSuperHero = true
}
SuperHero.prototype.fightCrime = function () {
    console.log('fighing crime')
}
SuperHero.prototype = Object.create(Person.prototype)
SuperHero.prototype.constructor = SuperHero

const batman = new SuperHero('bruce', 'wayne')
batman.sayMyName()
```

#### with classes

```js
class Person {
    constructor(firstName, lastName) {
        this.firstName = firstName
        this.lastName = lastName
    }

    sayMyName() {
        return this.firstName + " " + this.lastName
    }
}

const p1 = new Person('vishal', 'bhojane')
```

inheriting from Person

```js
class SuperHero extends Person {
    constructor(firstName, lastName) {
        super(firstName, lastName) // it will call Person class constructor
        this.isSuperHero = true
    }
    fightCrime() {
        console.log('fighing crime')
    }
}

const batman_usingClass = new SuperHero('bruce', 'wayne')
```