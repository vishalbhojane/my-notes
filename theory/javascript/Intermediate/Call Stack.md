JavaScript uses a Call Stack to track the functions in a program.

The call stack works on the Last In, First Out (LIFO) principle.
Most recently called function will be the first to be completed.
Whenever a function is called, a new frame is added to the top of the stack

```js
function greeting() {
    // [1] Some code here
    sayHi();
    // [2] Some code here
}
function sayHi() {
    return "Hi!";
}
greeting();
```

```
- Empty stack

- greeting

- sayHi
- greeting

- greeting

- Empty stack
```