*Classes are syntactical sugar over prototypal inheritance (ES6)*

Classes are a template for creating objects
They encapsulate data with code to work on that data
Classes in JS are built on prototypes

With the introduction of ES6, JavaScript now offers a more concise and readable way to define [[Constructor Functions]] using the class syntax.
A class constructor is a special method within a class that initializes objects.

In this example, the Car class has a constructor method that initializes the object and a `getDetails` method defined directly within the class body

```js
class Car {
    constructor(make, model, year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }

    getDetails() {
        return `${this.make} ${this.model} (${this.year})`;
    }
}

// Creating an object using the class constructor
let myCar = new Car('Toyota', 'Corolla', 2020);

console.log(myCar);
// Output: Car { make: 'Toyota', model: 'Corolla', year: 2020 }
```

### Static Methods

Static methods are defined using the static keyword

```js
class Car {
    constructor(make, model, year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }

    static calculateAge(year) {
        return new Date().getFullYear() - year;
    }
}
```

### Inheritance

Inheritance is more straightforward using the extends keyword

```js
class ElectricCar extends Car {
    constructor(make, model, year, batteryLife) {
        super(make, model, year);
        this.batteryLife = batteryLife;
    }
}
```

---
### Refactoring an Old Constructor Function with Modern Features

```js
// libraryConstructor.js

// Book constructor function
function Book(title, author, year) {
    this.title = title;
    this.author = author;
    this.year = year;
}

// Adding a method to the prototype
Book.prototype.getSummary = function() {
    return `${this.title} by ${this.author}, published in ${this.year}`;
};

// EBook constructor function inheriting from Book
function EBook(title, author, year, fileSize) {
    Book.call(this, title, author, year);
    this.fileSize = fileSize;
}

// Setting up inheritance
EBook.prototype = Object.create(Book.prototype);
EBook.prototype.constructor = EBook;

// Adding a method to the prototype
EBook.prototype.getFileSize = function() {
    return `${this.title} file size: ${this.fileSize}MB`;
};

// Creating objects
let myBook = new Book('1984', 'George Orwell', 1949);
let myEBook = new EBook('Digital Fortress', 'Dan Brown', 1998, 5);

console.log(myBook.getSummary()); // Output: 1984 by George Orwell, published in 1949
console.log(Book.calculateAge(myBook.year)); // Output: 75 (if current year is 2024)
console.log(myEBook.getFileSize()); // Output: Digital Fortress file size: 5MB
```

Refactored Code (Class Constructors)

```js
// libraryClass.js

// Importing a hypothetical decorator
function logMethod(target, propertyKey, descriptor) {
    const originalMethod = descriptor.value;

    descriptor.value = function(...args) {
        console.log(`Calling ${propertyKey} with arguments: ${JSON.stringify(args)}`);
        return originalMethod.apply(this, args);
    };

    return descriptor;
}

// Book class
class Book {
    // Private fields
    #title;
    #author;
    #year;

    constructor(title, author, year) {
        this.#title = title;
        this.#author = author;
        this.#year = year;
    }

    // Method within the class
    getSummary() {
        return `${this.#title} by ${this.#author}, published in ${this.#year}`;
    }

    // Static method
    static calculateAge(year) {
        return new Date().getFullYear() - year;
    }
}

// EBook class inheriting from Book
class EBook extends Book {
    // Private field
    #fileSize;

    constructor(title, author, year, fileSize) {
        super(title, author, year);
        this.#fileSize = fileSize;
    }

    // Decorated method to log method calls
    @logMethod
    getFileSize() {
        return `${this.#title} file size: ${this.#fileSize}MB`;
    }
}

// Creating objects
let myBook = new Book('1984', 'George Orwell', 1949);
let myEBook = new EBook('Digital Fortress', 'Dan Brown', 1998, 5);

console.log(myBook.getSummary()); // Output: 1984 by George Orwell, published in 1949
console.log(Book.calculateAge(myBook.year)); // Output: 75 (if current year is 2024)
console.log(myEBook.getFileSize()); // Output: Digital Fortress file size: 5MB
```

---
### Decorators Improve the Code

Decorators are a special kind of declaration that can be attached to classes, methods, properties, or parameters to modify their behavior. They provide a clean way to add additional functionality to a method or class without altering its core logic.

Example Use Case:
- Logging: Automatically log every time a method is called.
- Validation: Validate input data before executing a method.

In our example, we’ll use a hypothetical logMethod decorator that logs method calls.

---
### Private Fields

Private fields in ES6 classes, denoted by #, are used to encapsulate data, ensuring that these fields are not accessible outside the class. This promotes better encapsulation and data hiding, making the code more secure and easier to maintain.

Example Use Case:
- Encapsulation: Keep internal details of a class hidden from the outside, preventing accidental or unauthorized access.





