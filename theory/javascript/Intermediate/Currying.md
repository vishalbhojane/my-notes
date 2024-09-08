Currying is defined as changing a function having multiple arguments into a sequence of functions with a single argument

normal function with multiple arguments

```js
let multiply = function (x, y) {
    return x * y
}

let multiplyByTwo = function (y) {
    return 2 * y
}
```

### Currying using `bind()` method

```js
let multiplyByTwo_Bind = multiply.bind(this, 2);
multiplyByTwo_Bind(3)
```

### Currying using closures

```js
let multiplyNew = function (x) {
    return function (y) {
        return x * y
    }
}

let multiplyByTwo_Closure = multiplyNew(2)
multiplyByTwo_Closure(3)
```