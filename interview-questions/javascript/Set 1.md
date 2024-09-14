### Question: Explain event delegation.
Answer: Event delegation is a technique where you attach a single event listener to a parent element to handle events for its children. It's useful for dynamically added elements and improves performance by reducing the number of event listeners.

### Question: Explain how this works in JavaScript.
Answer: In JavaScript, 'this' refers to the current execution context. Its value depends on how a function is called:
- In a method, 'this' refers to the object.
- In a regular function, 'this' refers to the global object (or undefined in strict mode).
- In an arrow function, 'this' retains the value from the enclosing lexical context.

### Question: Can you give an example of one of the ways that working with this has changed in ES6?
Answer: Arrow functions in ES6 lexically bind 'this' to the surrounding code's context. For example:

```javascript
const obj = {
  name: 'John',
  greet: function() {
    setTimeout(() => {
      console.log(`Hello, ${this.name}`);
    }, 1000);
  }
};
obj.greet(); // Outputs: "Hello, John"
```

### Question: Explain how prototypal inheritance works.
Answer: In JavaScript, objects can inherit properties and methods from other objects through their prototype chain. When accessing a property, JavaScript looks up the prototype chain until it finds the property or reaches the end of the chain.

### Question: What is the difference between a variable that is: null, undefined or undeclared?
Answer: 
- Null: Explicitly assigned to represent no value.
- Undefined: Variable declared but not assigned a value.
- Undeclared: Variable used without being declared.

### Question: How would you go about checking for any of these states?
Answer:
- For null: `if (variable === null)`
- For undefined: `if (typeof variable === 'undefined')`
- For undeclared: Use a try-catch block

### Question: What is a closure, and how/why would you use one?
Answer: A closure is a function that has access to variables in its outer lexical scope, even after the outer function has returned. It's used for data privacy, creating function factories, and implementing module patterns.

### Question: What language constructions do you use for iterating over object properties and array items?
Answer: 
- For arrays: for...of loop, forEach(), map(), filter(), reduce()
- For objects: for...in loop, Object.keys(), Object.values(), Object.entries()

### Question: Can you describe the main difference between the Array.forEach() loop and Array.map() methods and why you would pick one versus the other?
Answer: forEach() iterates over array elements without returning a new array, while map() creates a new array with the results of calling a function on every element. Use forEach() for side effects and map() when you need to transform array elements.

### Question: Can you describe other popular methods for iterating over arrays?
Answer: filter() for creating a new array with elements that pass a test, reduce() for reducing an array to a single value, find() for finding the first element that satisfies a condition, and some() to test if at least one element passes a test.

### : What is a typical use case for anonymous functions?
Answer: Anonymous functions are commonly used as callbacks, in event handlers, and for creating closures. They're also used in higher-order functions like map() or filter().

### Question: What is the difference between host objects and native objects?
Answer: Native objects are defined in the ECMAScript specification (e.g., Array, Object). Host objects are provided by the runtime environment (e.g., window, document in browsers).

### Question: Explain the difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
Answer:
- `function Person(){}` declares a function.
- `var person = Person()` calls the function and assigns its return value to person.
- `var person = new Person()` creates a new instance of Person, with person inheriting from `Person.prototype`.

### Question: Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`
Answer: function foo() {} is a function declaration, hoisted to the top. var foo = function() {} is a function expression, not hoisted. The variable declaration is hoisted, but the assignment isn't.

### Question: Can you explain what Function.call and Function.apply do? What is the notable difference between the two?
Answer: Both call() and apply() invoke a function with a specified this value. The difference is in how additional arguments are passed: call() takes them as separate arguments, while apply() takes them as an array.

### Question: Explain Function.prototype.bind.
Answer: bind() creates a new function with a fixed this value and optionally preset arguments. It's useful for ensuring a function is called with a specific context.

### Question: What is the difference between feature detection, feature inference, and using the UA string?
Answer:
- Feature detection: Checking if a feature exists.
```js
if ("geolocation" in navigator) {
  navigator.geolocation.getCurrentPosition(function (position) {
    // show the location on a map, such as the Google Maps API
  });
} else {
  // Give the user a choice of static maps
}
```
- Feature inference: Assuming related features exist based on one feature.
```js
if (document.getElementsByTagName) {
  element = document.getElementById(id);
}
```
- UA string: Identifying the browser based on the user agent string. `navigator.userAgent`
Feature detection is generally the most reliable approach.

### Question: Explain "hoisting".
Answer: Hoisting is JavaScript's behavior of moving declarations to the top of their scope. Function declarations and var variables are hoisted. let and const variables are hoisted but not initialized, creating a temporal dead zone.

### Question: What is type coercion? What are common pitfalls of relying on type coercion in JavaScript code?
Answer: Type coercion is the automatic conversion of values from one type to another. Pitfalls include unexpected results in comparisons (e.g., "0" == false is true) and potential performance issues.

### Question: Describe event bubbling.
Answer: Event bubbling is the process where an event triggers on the deepest target element, then propagates up through its ancestors in the DOM tree.

### Question: Describe event capturing.
Answer: Event capturing is the opposite of bubbling. The event is first captured by the outermost element and propagated to the inner elements. It's less commonly used than bubbling.

### Question: What is the difference between an "attribute" and a "property"?
Answer: Attributes are defined in HTML and properties are defined in the DOM. Properties can be dynamic, while attributes are static. Some attributes map directly to properties, but not all.

### Question: What are the pros and cons of extending built-in JavaScript objects?
Answer: 
Pros: Can add useful functionality to native objects.
Cons: Can lead to naming conflicts, unexpected behavior, and compatibility issues with future JavaScript versions.

### Question: What is the difference between `==` and `===`
Answer: == performs type coercion before comparison, while === compares without type coercion. === is generally preferred for its predictability and performance.

### Question: Explain the same-origin policy with regards to JavaScript.
Answer: The same-origin policy restricts how a document or script loaded from one origin can interact with a resource from another origin. It's a critical security mechanism to prevent malicious scripts.

### Question: Why is it called a Ternary operator, what does the word "Ternary" indicate?
Answer: The ternary operator is called so because it takes three operands. It's a shorthand for an if-else statement: condition ? expressionIfTrue : expressionIfFalse.

### Question: What is strict mode? What are some of the advantages/disadvantages of using it?
Answer: Strict mode is a way to opt in to a restricted variant of JavaScript. Advantages include catching errors earlier and preventing some unsafe actions. Disadvantages might include compatibility issues with older browsers.

### Question: What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
Answer: 
Advantages: Additional features, better tooling, type checking (e.g., TypeScript).
Disadvantages: Additional compilation step, potential debugging difficulties, learning curve.

### Question: What tools and techniques do you use debugging JavaScript code?
Answer: Browser DevTools (console, debugger), source maps, linters, unit tests, and debugging statements (console.log, debugger keyword).

### Question: Explain the difference between mutable and immutable objects.
Answer: Mutable objects can be changed after creation, while immutable objects cannot. In JavaScript, objects and arrays are mutable by default, while primitive values are immutable.

### Question: What is an example of an immutable object in JavaScript?
Answer: String objects are immutable in JavaScript. When you perform operations on a string, a new string is created rather than modifying the original.

### Question: What are the pros and cons of immutability?
Answer: 
Pros: Predictability, easier to track changes, thread-safety.
Cons: Memory usage (creating new objects), potential performance overhead.

### Question: How can you achieve immutability in your own code?
Answer: Use `const` for declarations,` Object.freeze()` for shallow immutability, or libraries like Immutable.js for deep immutability. Avoid direct mutations and use spread operators or `Object.assign()` for creating new objects.

### Question: Explain the difference between synchronous and asynchronous functions.
Answer: Synchronous functions block execution until they complete, while asynchronous functions allow the program to continue executing while they perform their task.

### Question: What is event loop?
Answer: The event loop is a mechanism that allows JavaScript to perform non-blocking operations despite being single-threaded. It continuously checks the call stack and callback queue, executing tasks when the stack is empty.

### Question: What is the difference between call stack and task queue?
Answer: The call stack tracks function calls in the code. The task queue holds callbacks from asynchronous operations. The event loop moves tasks from the queue to the stack when it's empty.

### Question: What are the differences between variables created using let, var or const?
Answer: 
- var: function-scoped, hoisted
- let: block-scoped, not hoisted (temporal dead zone)
- const: block-scoped, not hoisted, cannot be reassigned

### Question: Can you change a property of an object defined via const? How you can change this behavior?
Answer: Yes, you can change properties of a const object. To prevent this, use Object.freeze() for shallow immutability or deep freeze libraries for nested objects.

### Question: What are the differences between ES6 class and ES5 function constructors?
Answer: ES6 classes provide a cleaner syntax for creating objects and implementing inheritance. They are syntactic sugar over ES5 prototypal inheritance but with some differences in hoisting and strict mode behavior.

### Question: Can you offer a use case for the new arrow => function syntax? How does this new syntax differ from other functions?
Answer: Arrow functions are useful for short, anonymous functions, especially as callbacks. They have a lexical 'this' binding, shorter syntax, and cannot be used as constructors.

### Question: What advantage is there for using the arrow syntax for a method in a constructor?
Answer: Arrow functions in constructors maintain the 'this' context of the instance, avoiding the need for '.bind(this)' or saving 'this' to a variable.

### Question: What is the definition of a higher-order function?
Answer: A higher-order function is a function that takes one or more functions as arguments or returns a function as its result.

### Question: Can you give an example for destructuring an object or an array?
Answer: 
Object destructuring: const {name, age} = person;
Array destructuring: const [first, second] = array;

### Question: Can you give an example of generating a string with ES6 Template Literals?
Answer: const greeting = `Hello, ${name}! You are ${age} years old.`;

### Question: Can you give an example of a curry function and why this syntax offers an advantage?
Answer: 
const add = a => b => a + b;
const add5 = add(5);
console.log(add5(3)); // 8

Advantage: Allows partial application of a function's arguments, enhancing reusability and composition.

### Question: What are the benefits of using spread syntax and how is it different from rest syntax?
Answer: Spread (...) expands an iterable into individual elements. Rest collects multiple elements into an array. Spread is used in function calls and array/object literals, while rest is used in function parameters and destructuring.

### Question: How can you share code between files?
Answer: Using ES6 modules (import/export), CommonJS (require/module.exports), or AMD (define/require) depending on the environment.

### Question: Why you might want to create static class members?
Answer: Static members belong to the class itself, not instances. They're useful for utility functions, constants, or data shared across all instances of a class.

### Question: What is the difference between while and do-while loops in JavaScript?
Answer: A while loop checks the condition before executing the loop body, while a do-while loop executes the body at least once before checking the condition.

### Question: What is a promise? Where and how would you use promise?
Answer: A promise is an object representing the eventual completion or failure of an asynchronous operation. It's used for handling asynchronous operations more cleanly than callbacks, such as in API calls or file operations.

### Question: Discuss how you might use Object Oriented Programming principles when coding with JavaScript.
Answer: JavaScript supports OOP through prototypes and classes. You can use encapsulation (private variables), inheritance (extends keyword), and polymorphism (method overriding). Composition can be achieved by combining objects.

### Question: What is the difference between event.target and event.currentTarget?
Answer: event.target is the element that triggered the event, while event.currentTarget is the element that the event listener is attached to. They may differ during event bubbling.

### Question: What is the difference between event.preventDefault() and event.stopPropagation()?
Answer: 
- event.preventDefault() stops the default action of an event (e.g., form submission).
- event.stopPropagation() stops the event from bubbling up the DOM tree.