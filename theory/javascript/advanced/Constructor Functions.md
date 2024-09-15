A constructor function is a regular function used in conjunction with the `new` keyword to initialize a new object.

In this example, the Car function initializes a new car object with make, model, and year properties.

```js
function Car(make, model, year) {
    this.make = make;
    this.model = model;
    this.year = year;
}

// Creating an object using the constructor function
let myCar = new Car('Toyota', 'Corolla', 2020);

console.log(myCar);
// Output: Car { make: 'Toyota', model: 'Corolla', year: 2020 }
```

### Adding Methods to Constructor Function

To add methods to a constructor function, we use the `prototype` property

```js
Car.prototype.getDetails = function() {
    return `${this.make} ${this.model} (${this.year})`;
};

// Using the method
console.log(myCar.getDetails()); // Output: Toyota Corolla (2020)
```

### Static Methods

Static methods are added directly to the constructor function.

```js
Car.calculateAge = function(year) {
    return new Date().getFullYear() - year;
};
```

### Inheritance

Inheritance is achieved through prototypal inheritance

```js
function ElectricCar(make, model, year, batteryLife) {
    Car.call(this, make, model, year);
    this.batteryLife = batteryLife;
}
ElectricCar.prototype = Object.create(Car.prototype);
ElectricCar.prototype.constructor = ElectricCar;
```
