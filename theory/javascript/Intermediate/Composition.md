Function composition is the process of chaining together multiple functions to form a new function

It involves applying a series of transformations or operations to an input value, where the output of one function becomes the input of the next function in the composition chain.

The compose function takes in two or more functions and returns a new function that applies these functions in right-to-left order

This means that the rightmost function is applied first, followed by the next function to its left, and so on

```js
const add5 = (x) => x + 5;
const multiplyBy3 = (x) => x * 3;
const subtract10 = (x) => x - 10;

const composedFunction = compose(subtract10, multiplyBy3, add5);
const result = composedFunction(7);
```

Implementing a compose function

```js
const compose = function(...fns){
    return function(input){
        return fns.reduceRight((acc, curr) => curr(acc), input)
    }
}
```


#### Reusability
By composing smaller, reusable functions, we can create complex operations without duplicating code. Each function can focus on a specific task, promoting code modularity and reusability.

#### Readability
Function composition allows us to express complex operations in a more declarative and concise manner. By chaining functions together, we can describe the intended transformation in a way that closely aligns with the problem domain.

#### Maintainability
Since each function has a well-defined purpose, it becomes easier to understand, test, and modify individual functions. Changes to one function do not impact other functions in the composition, leading to code that is easier to maintain and reason about.