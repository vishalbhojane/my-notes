Create an ArrayWrapper class with the following features:
1. Constructor accepts an array of integers.
2. When two instances are added with '+', return the sum of all elements in both arrays.
3. When String() is called on an instance, return a comma-separated string of elements in brackets.
## Solution

```javascript
class ArrayWrapper {
    constructor(nums) {
        this.nums = nums;
    }

    valueOf() {
        return this.nums.reduce((sum, num) => sum + num, 0);
    }

    toString() {
        return `[${this.nums.join(',')}]`;
    }
}
```

Usage

```javascript
const obj1 = new ArrayWrapper([1,2]);
   const obj2 = new ArrayWrapper([3,4]);
   obj1 + obj2; // 10
```

```javascript
const obj = new ArrayWrapper([23,98,42,70]);
   String(obj); // "[23,98,42,70]"
```