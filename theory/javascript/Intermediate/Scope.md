The scope is a policy that manages the availability of variables.

A variable defined inside a scope is accessible only within that scope, but inaccessible outside.
In JavaScript, **scopes are created by code blocks, functions, modules**

Every time you have curly braces `{}`, you are working inside of particular scope.
most outer is Global scope.
Different scope can have similar variable names

### JavaScript variables have 3 types of scope:
Global scope: most outer scope
Function scope: `function(){}`
Block scope: `{}`, `let` and `const` follows block scope

#### Global scope
Accessible everywhere

```js
let x = 1;
```

#### Function scope

```js
// code here can NOT use carName
function myFunction() {
    let carName = "Volvo";
    // code here CAN use carName
}
// code here can NOT use carName
```

#### Block scope

```js
{
    let x = 2;
}
console.log(x);
// ReferenceError: x is not defined
```

## Scope Chain

Hierarchical structure that determines the order in which Javascript looks for variables is called a Scope Chain

When a variable is accessed, Javascript first searches for it in the current scope
and if it's not found, it moves up the scope chain until the variable is found or the global scope is reached.

```js
let g = 1
// can access only g
{
    let a = 2
    // can access only a and g
    {
        let b = 3
        // can access a,b,g
    }
}
```