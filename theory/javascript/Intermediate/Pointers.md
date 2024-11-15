```js
let num1 = 10
let num2 = num1

console.log(num2) // 10

num1 = 5

console.log(num2) // 10
```

Here `num2` gets value of `num1` during execution phase (in memory creation variables are created and set the value as undefined)
Hence changing the value of `num1` does not affect `num2` even if we have assigned it as
`num2 = num1`

---
### Using Pointers in JavaScript

```js
let obj1 = {
    value: 11
}

let obj2 = obj1

console.log(obj2.value) // 11

obj1.value = 12

console.log(obj2.value) // 12

obj2.value = 13

console.log(obj1) // 13
```

Here `obj2` is pointing to same object in memory as `obj1`
Hence changing the value of `obj1` affects `obj2` and vice verse

```js
let obj1 = {
    value: 11
}

let obj2 = {
    value: 12
}

obj1 = obj2
```

In above code `obj1` is now pointing to `obj2` the, initial `object` that was assigned to `obj1` now has no reference, and now it's just taking up memory
Hence garbage collector will remove that `object`