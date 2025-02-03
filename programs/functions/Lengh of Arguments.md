Create a function `argumentsLength` that returns the number of arguments passed to it, regardless of their types.

```javascript
function argumentsLength(...args) {
    return args.length;
}
```

Usage

```javascript
console.log(argumentsLength(5)); // 1
console.log(argumentsLength({}, null, "3")); // 3
console.log(argumentsLength(1, 2, 3)); // 3
console.log(argumentsLength()); // 0
```