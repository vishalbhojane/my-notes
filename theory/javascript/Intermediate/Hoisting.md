Hoisting - (`var` and `function`)
Hoisting is JavaScript's default behaviour of moving all `var` and `function` declarations to the top of the current scope before code execution. (*to the top of the current script or the current function*)


```js
console.log(sum(1, 2))
console.log(c)
function sum(a, b) { return a + b }
var c = 2
```

After hoisting it becomes

```js
function sum(a, b) { return a + b }
var c = undefined
console.log(sum(1, 2))
console.log(c) // undefined
c = 2
```

`var` is partially hosted, `function` declaration are fully hoisted

**Note**: Hoisting does not work with arrow function, and will return reference error. because arrow functions are defined as a variable i.e. using `let`,`const` keyword