What will the code below output to the console and why?

```js
(function(){
  var a = b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));
```

Output

```
a defined? false
b defined? true
```

Explanation: `a` is local to `IIFE` as it is declared using `var`, `b` is not declared using `var`, hence global variable is created when `IIFE` executes

## Consider the two functions below. Will they both return the same thing? Why or why not?

```js
function foo1()
{
  return {
      bar: "hello"
  };
}

function foo2()
{
  return
  {
      bar: "hello"
  };
}
```

Answer: check `foo2`, object starts on different line, line after `return` never runs
