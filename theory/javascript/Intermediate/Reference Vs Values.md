objects and arrays store references

values

```js
let value1 = 1;
let value2 = value1;
value2 = value2 + 2;
console.log(value1); // 1
console.log(value2); // 3
```

reference

```js
let x = [1]; // assume memory addres 0x01
let y = x; // gets the same memory address 0x01
y.push(2); // value at 0x01 is changed 
console.log(x); // [1, 2]
console.log(y); // [1, 2]
```

comparing values

```js
const one = 1;
const oneCopy = 1;
console.log(one === oneCopy); // true
console.log(one === 1);       // true
console.log(one === one);     // true
```

comparing references

```js
const ar1 = [1];
const ar2 = [1];
console.log(ar1 === ar2); // false, because reference is in different place in memory
console.log(ar1 === [1]);  // false
const ar11 = ar1;
console.log(ar1 === ar11); // true
console.log(ar1 === ar1);  // true
```

#### Why? 😐

```js
const arr1 = [1, 2] // 0x01
const arr2 = [1, 2] // 0x02
arr1.push(3)
```
will not throw error even it looks like we are changing the const.
actually we are modifying the value at that memory address. not the actual address. `const` doesn't care about what is there at memory address

only way to change the address is

```js
arr1 = [1, 2, 3]
// TypeError: Assignment to constant variable.
```

pass by reference with function

```js
const arr3 = [1, 2] // at memory address 0x01
const elementToPush = 3 // hard value 3

function add(array, element) {
    element = element + 1 // 4, at local scope of add function.
    array.push(element) // modifies value at location 0x01 by pushing the (element = element + 1 ,i.e 4)
}

add(arr1, elementToPush) // takes address 0x01 and hard value 3 as arguments

console.log(arr1) // [1,2,4]
console.log(elementToPush) // 3
```