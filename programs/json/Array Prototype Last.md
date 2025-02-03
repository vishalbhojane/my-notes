Extend the Array prototype to include a last() method that returns the last element of the array. If the array is empty, it should return -1.

```javascript
Array.prototype.last = function() {
    return this.length ? this[this.length - 1] : -1;
};
```

Usage

```javascript
const arr1 = [null, {}, 3];
console.log(arr1.last()); // 3

const arr2 = [];
console.log(arr2.last()); // -1

const arr3 = [1, 2, 3, 4, 5];
console.log(arr3.last()); // 5
```