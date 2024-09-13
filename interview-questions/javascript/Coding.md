### Question: What is the value of foo?
var foo = 10 + '20';
Answer: The value of foo is '1020'. JavaScript coerces the number 10 to a string and performs string concatenation.

### Question: What will be the output of the code below?
console.log(0.1 + 0.2 == 0.3);
Answer: The output will be false. Due to floating-point precision issues in JavaScript, 0.1 + 0.2 is slightly more than 0.3.

### Question: How would you make this work?
add(2, 5); // 7
add(2)(5); // 7
Answer: 

```javascript
function add(x) {
  if (arguments.length === 2) {
    return arguments[0] + arguments[1];
  }
  return function(y) {
    return x + y;
  };
}
```

### Question: What value is returned from the following statement?
`"i'm a lasagna hog".split("").reverse().join("");`
Answer: "goh angasal a m'i". The string is split into an array of characters, reversed, and joined back into a string.

### Question: What is the value of window.foo?
`( window.foo || ( window.foo = "bar" ) );`
Answer: The value of `window.foo` will be "`bar`". If `window.foo` is falsy, it's assigned "`bar`".
Also check operator precedence

### Question: What is the outcome of the two alerts below?
```js
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```
Answer: The first alert shows "Hello World". The second alert throws a ReferenceError because bar is not defined in the global scope.

### Question: What is the value of foo.length?
```js
var foo = [];
foo.push(1);
foo.push(2);
```
Answer: foo.length is 2. Two elements have been pushed into the array.

### Question: What is the value of foo.x?
```js
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
```
Answer: foo.x is `undefined`. The assignment is evaluated right-to-left, so foo is reassigned before foo.x is set.

### Question: What does the following code print?
```js
console.log('one');
setTimeout(function() {
  console.log('two');
}, 0);
Promise.resolve().then(function() {
  console.log('three');
})
console.log('four');
```
Answer: It prints: 'one', 'four', 'three', 'two'. Promises are microtasks and have priority over setTimeout callbacks.

### Question: What is the difference between these four promises?
Answer: 
1. Returns a promise that resolves to the result of doSomethingElse().
2. Returns a promise that resolves to undefined.
3. Immediately executes doSomethingElse() and passes its result to then().
4. Passes the doSomethingElse function as a callback to then().

### Question: What will the code below output to the console and why?
```js
(function(){
  var a = b = 3;
})();
console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));
```
Answer: It outputs:
"a defined? false"
"b defined? true"
'a' is locally scoped, while 'b' becomes a global variable due to lack of 'var'.

### Question: Consider the two functions below. Will they both return the same thing? Why or why not?
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
Answer: They return different things. foo1() returns an object {bar: "hello"}, while foo2() returns undefined due to automatic semicolon insertion after the return statement.