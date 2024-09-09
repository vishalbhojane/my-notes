Closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment).
Closure gives you access to an outer function’s scope from an inner function.

**Imp**: To use a closure, define a function inside another function and expose it. To expose a function, return it or pass it to another function.

You can always read things outside of where you are but you can never read things inside

```js
function x() {
    var a = 7;
    function y() {
        // debugger;
        console.log(a)
    }
    return y;
}
var z = x();
```

Different syntax

```js
function x() {
    var a = 7;
    return function y() {
        console.log(a)
    }
}
var z = x()
```

Function returned from `x()` is stored in `var` `z`, it will also remember its lexical scope even if `x` is done executing and no longer on call stack

#### Corner case 1

```js
function x() {
    var a = 7;
    function y() {
        // debugger;
        console.log(a) // here value of a (i..e. a = 7) is not persisted, but the reference to 'a' is persisted
    }
    a = 100;
    return y;
}
var res = x();
res(); // we will get 100 as output
```

#### Chaining Continues

```js
function w() {
    var b = 2;

    return function x() {
        var a = 7

        return function y() {
            console.log(b, a);
        }
    }
}
var res = w();
```

#### Uses of closures
- Module design pattern
- Currying
- Functions like 'once' / To make function run only once 
- Memoize
- Maintaining state in async world
- setTimeouts
- Iterators
- and many more...