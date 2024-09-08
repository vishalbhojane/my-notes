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

## Example 2

```js
function f1() {
    console.log('Hi by f1!');
}

function f2() {
    f1();
    console.log('Hi by f2!');
}

f2();
```

1. When the code loads in memory, the global execution context gets pushed in the stack

```
// global execution context
```

2. The f2() function gets called, and the execution context of f2() gets pushed into the stack.

```
// function f2() {
//     f1();
//     console.log('Hi by f2!');
// }
// global execution context
```

3. Step 3: The execution of f2() starts and during its execution
the f1() function gets called inside the f2() function.
This causes the execution context of f1() to get pushed in the call stack

```
// function f1() {
//     console.log('Hi by f1!');
// }
// function f2() {
//     f1();
//     console.log('Hi by f2!');
// }
// global execution context
```

4. Step 4: Now the f1() function starts executing.
A new stack frame of the console.log() method will be pushed to the stack.

```
// console.log('Hi by f1!');
// function f1() {
//     console.log('Hi by f1!');
// }
// function f2() {
//     f1();
//     console.log('Hi by f2!');
// }
// global execution context
```

5. When the console.log() method runs, it will print “Hi by f1” and then it will be popped from the stack.
The execution context will go back to the function and now there are no lines of code that remain in the f1() function, and as a result, it will be popped from the call stack.

6. This will similarly happen with the console.log() method that prints the line “Hi by f2” and then finally the function f2() would finish and would be pushed off the stack.