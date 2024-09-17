##### Event delegation
[[Event Delegation]]

##### Explain how this works in JavaScript
[[This Keyword]]

##### Explain how prototypal inheritance works
[[Inheritance]]

##### What is the difference between a variable that is: `null`, `undefined` or undeclared?
`null`: Explicitly assigned to represent no value.
`undefined`: Variable declared but not assigned a value.
undeclared: Variable used without being declared

##### How would you go about checking for any of these states
`null`: `if (variable === null)`
`undefined`: `if (typeof variable === 'undefined')`
undeclared: Use a try-catch block

##### What language constructions do you use for iterating over object properties and array items?
For arrays: `for...of` loop, `forEach()`, `map()`, `filter()`, `reduce()`
For objects: `for...in` loop, `Object.keys()`, `Object.values()`, `Object.entries()`

##### Difference between the `Array.forEach()` loop and `Array.map()` methods and why you would pick one versus the other?
`forEach()` iterates over array elements without returning a new array
`map()` creates a new array with the results of calling a function on every element
Use `forEach()` for side effects and `map()` when you need to transform array elements

##### Use case for anonymous functions?
Anonymous functions are commonly
Used as callbacks, in event handlers, and for creating closures.
Used in higher-order functions like map() or filter()

##### Difference between host objects and native objects?
Native objects are defined in the `ECMAScript` specification (e.g., Array, Object)
Host objects are provided by the runtime environment (e.g., `window`, `document` in browsers)

##### Explain the difference between:
`function Person(){}`
Defines a constructor function called Person

`var person = Person()`
Calls `Person` as a regular function (not as a constructor), resulting in `person` being `undefined` (or whatever `Person` returns if there is an explicit return)

`var person = new Person()`?
Calls `Person` as a constructor, creating and returning a new object that is an instance of `Person`

##### Explain the differences on the usage of `foo` between
`function foo() {}` 
Function Declaration
Hoisted completely; can be called before its declaration
Accessible throughout its containing scope

`var foo = function() {}`
Function Expression
Only the variable (foo) is hoisted; calling foo() before the assignment results in an error
The function is defined only after the assignment, affecting its availability in the scope

##### Explain `Function.call` and `Function.apply` and differences
##### Explain `Function.prototype.bind`
[[Call Apply Bind]]

##### Difference between feature detection, feature inference, and using UA string
[[Polyfills]]
UA string: Identifying the browser based on the user agent string. `navigator.userAgent`
Feature detection is generally the most reliable approach

##### Explain hoisting
[[Hoisting]]

##### Type Coercion
[[Type Coercion]]

##### Event Bubbling, Capturing
[[Bubble and Capture]]


