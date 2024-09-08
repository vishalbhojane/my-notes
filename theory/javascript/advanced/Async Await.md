*another way to handle promise*
JavaScript Introduces keywords `async` and `await` in ES6

### `Async`
When we append the keyword `async` to the function, this function returns the Promise by default on execution
```js
async function simpleAsync() {
    return "hello"
}
console.log(simpleAsync())
// Promise {<fulfilled>: 'hello'}
```

`Async` keyword provides extra information to the user of the function
  - The function contains some Asynchronous Execution
  - The returned value will be the Resolved Value for the Promise

We can associate a callback function with the promise using “`then`”
```js
simpleAsync().then((data) => {
    console.log(data)
})
// hello
```

**summery**
Appending “`async`” will return a promise from a function
In case the function is returning some value, the value will be available as the resolved value from the promise.
If no value is returned, the resolved value will be “undefined”

#### Understanding Asynchronous Execution
```js
function returnPromises() {
    var newPromise = new Promise((resolve) => {
        setTimeout(() => {
            console.log("Promise Executed...");
            resolve("Sample Data");
        }, 3000);
    });
}

function executeFunction() {
    var newData = "hello";
    var getPromise = returnPromises();
    console.log(newData);
}

executeFunction()
// hello (console.log(newData) displayed before the promise)
// undefined (output during promise is being resolved)
// Promise Executed...
```

## `Await`
Adding “`await`” before a promise makes the execution thread to wait for asynchronous task/promise to resolve before proceeding further
it introduces **synchronous behavior** to the application. Even the promises will be executed synchronously

```js
function returnPromises() {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("Promise Executed...");
            resolve("Sample Data");
        }, 3000);
    });
}

async function executeFunction() {
    try {
        var newData = "Vishal";
        console.log(newData)
        var getData = await returnPromises();
        console.log(getData);
    } catch (error) {
        console.log(error)
    }
}

executeFunction()
// Vishal
// Promise {<pending>}
// Promise Executed...
// Sample Data
```

`Await` and `Async` keyword combined together ensures that the main thread will not start executing further until the asynchronous part of the application has finished execution
hence imparting synchronous behaviour to the thread.

### more ex
```js
function setTimeoutPromise(delay) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            // resolve(`You waited ${delay} milliseconds`)
            reject("Error!")
        }, delay)
    })
}

// using promise
setTimeoutPromise(100)
    .then(message => {
        console.log(message)
        console.log("1")
        return setTimeoutPromise(100)
    })
    .then(message => {
        console.log(message)
        console.log("2")
    })
    .catch(e => {
        console.error(e)
    })
```

```js
// using async
async function doStuff() {
    try {
        console.log("before error")
        const message = await setTimeoutPromise(100) // wait until this promise executes and resolve, and then continue executing the code, while this execute JS does executes
        console.log("after error") //here from this line it will no execute because our promise is rejected
        console.log(message)
        console.log("1")
        const message2 = await setTimeoutPromise(100)
        console.log(message2)
        console.log("2")
    } catch (error) {
        console.error(error)
    } finally { //executes not matter...
        console.log("finally")
    }
}
doStuff()
// before error
// Promise {<pending>}
// Error!
// finally
```
### more ex

```js
function getValueWithDelay(value, delay) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(value)
        }, delay)
    })
}

async function doStuff() {
    for (let i = 0; i < 10; i++) {
        const value = await getValueWithDelay(i)
        console.log(value)
    }
}
doStuff()
// this code will take longer to execute, 250ms for each iteration

// fix using promise, becuse promises run parallel if you are not chaining them
for (let i = 0; i < 10; i++) {
    getValueWithDelay(i).then(value => {
        console.log(value)
    })
}
// here everything will print out after 250 ms
```