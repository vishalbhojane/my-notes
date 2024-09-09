## What is the value of `foo`?

```js
var foo = 10 + '20';
console.log(foo)
```

Answer: `"1020"`
Explanation: type coercion

## What will be the output of the code below?

```js
console.log(0.1 + 0.2 == 0.3);
```

Answer: `false`
Explanation: "floating point error" or "rounding error",  Due to this error, adding two small numbers like `0.1` and `0.2`, both of which are less than `0.5`, may not result in an exact sum equal to `0.3`.

## How would you make this work?

```js
add(2, 5); // 7
add(2)(5); // 7
```

Answer

```js
function add(a){
	return function(b){
		return a + b
	}
}

console.log(add(2)(5))
```

More Generic *function currying*

```js
function add(a){
	return function(b){
		if(!b) {
			return a
		}
		return add(a, b) 
	}
}
```

## What value is returned from the following statement?

```js
const result = "i'm a lasagna hog".split("").reverse().join("")
console.log(result)
```

Answer: `"goh angasal a m'i"`

## What is the value of `window.foo`?

```js
( window.foo || ( window.foo = "bar" ) )
```

Answer: 'bar'
Explanation: Operator precedence, `( )` will executed first 

## What is the outcome of the two alerts below?

```js
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```

Answer: first `alert` inside `iife` will output "Hello World", then it will give reference error for second `alert`

## What is the value of `foo.length`?

```js
var foo = [];
foo.push(1);
foo.push(2);
```

Answer: 2

## What is the value of `foo.x`?

```js
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
```

Answer: `undefined`, property `x` does not exists in `foo`

## What does the following code print?

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

Answer:

```
one
four
three
two
```

