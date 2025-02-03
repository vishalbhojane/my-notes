Design a Calculator class with the following methods:
- Constructor: Accepts an initial value
- add(value): Adds value to result
- subtract(value): Subtracts value from result
- multiply(value): Multiplies result by value
- divide(value): Divides result by value (throw error if value is 0)
- power(value): Raises result to the power of value
- getResult(): Returns the current result

All methods except getResult should return the Calculator instance for method chaining.
## Solution

```javascript
class Calculator {
    constructor(value) {
        this.value = value;
    }
    
    add(value) {
        this.value += value;
        return this;
    }
    
    subtract(value) {
        this.value -= value;
        return this;
    }
    
    multiply(value) {
        this.value *= value;
        return this;
    }
    
    divide(value) {
        if (value === 0) throw new Error("Division by zero is not allowed");
        this.value /= value;
        return this;
    }
    
    power(value) {
        this.value **= value;
        return this;
    }
    
    getResult() {
        return this.value;
    }
}
```