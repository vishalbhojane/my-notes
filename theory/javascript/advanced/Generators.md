A generator function is a special type of function that can pause its execution and resume later.
They are defined using the` function*` syntax and use the yield keyword to yield values.

A generator function uses the `yield` keyword to generate values, pausing execution and sending values to the caller
It retains the state to resume execution after yield, continuing immediately after the last yield run

Generator functions return a generator object.
Generator objects are used either by calling the next method on the generator object
or using the generator object in a “`for of`” loop

```js
function* fun() {
    yield 10;
    yield 20;
    yield 30;
}

let gen = fun();
console.log(gen.next().value);
// 10
console.log(gen.next().value);
// 20
console.log(gen.next().value);
// 30
```

This example code prints infinite series of natural numbers using a simple generator

```js
function* nextNatural() {
    let naturalNumber = 1;

    // Infinite Generation
    while (true) {
        yield naturalNumber;
        naturalNumber++;
    }
}

// Calling the Generate Function
let gen2 = nextNatural();

// Loop to print the first 10 Generated number
for (let i = 0; i < 10; i++) {
    // Generating Next Number
    console.log(gen2.next().value);
}
```

## `yield`
pauses the generator execution and returns the value of the expression which is being written after the yield keyword.

## `yield*`
it iterates over the operand and returns each value until done is true

```js
const arr = ['a', 'b', 'c'];

function* generator() {
    yield 1;
    yield* arr;
    yield 2;
}
const gen4 = generator();
for (let value of gen4) {
    console.log(value);
}
// 1
// a
// b
// c
// 2
```

Return from a generator function

```js
function* generator() {
    yield 'a';
    return 'result';
    yield 'b';
}

let gen5 = generator();
console.log(JSON.stringify(gen5.next()));
// {value: "a", done: false}
console.log(JSON.stringify(gen5.next()));
// {value: "result", done: true}
```

Manually return from a generator

```js
let array = ['a', 'b', 'c'];
function* generator(arr) {
    let i = 0;
    while (i < arr.length) {
        yield arr[i++]
    }
}

const gen3 = generator(array);
// We can do gen3.return() to finish the generator
```

Throw an exception from the generator

```js
function* generator() {
    throw new Error('Error Occurred');
}
const gen6 = generator();
gen6.next();
```

Calling a generator from another generator

```js
function* firstGenerator() {
    yield 2;
    yield 3;
}
function* secondGenerator() {
    yield 1;
    yield* firstGenerator();
    yield 4;
}
for (let value of secondGenerator()) {
    console.log(value)
}
```

### Limitation of Generators:
You can’t yield inside a callback in a generator.

```js
function* generator() {
    ['a', 'b', 'c'].forEach(value => yield value) 
    // This will give syntax error
}
```


## `async function*()`
Using `async` generators (for api call)

```js
const firstPromise = () => {
    return new Promise((resolve, reject) => { setTimeout(() => resolve(1), 5000) })
}
const secondPromise = () => {
    return new Promise((resolve, reject) => { setTimeout(() => resolve(2), 3000) })
}

async function* generator() {
    const firstPromiseResult = await firstPromise();
    yield firstPromiseResult;
    const secondPromiseResult = await secondPromise();
    yield secondPromiseResult;
}

let gen7 = generator();
for await (let value of gen7) {
    console.log(value);
}
// (after 5 seconds)
// 1 
// (after 3 seconds)
// 2
```