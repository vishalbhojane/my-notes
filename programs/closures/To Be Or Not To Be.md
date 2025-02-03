Create a function `expect` that takes a value and returns an object with two methods:
1. `toBe(val)`: Returns true if the input equals val, otherwise throws "Not Equal".
2. `notToBe(val)`: Returns true if the input doesn't equal val, otherwise throws "Equal".

## Solution

```javascript
var expect = function(val) {
    return {
        toBe: (compareVal) => {
            if (val === compareVal) return true;
            throw new Error("Not Equal");
        },
        notToBe: (compareVal) => {
            if (val !== compareVal) return true;
            throw new Error("Equal");
        }
    };
};
```

Usage

```javascript
expect(5).toBe(5);     // true
expect(5).toBe(null);  // throws "Not Equal"
expect(5).notToBe(null); // true
```