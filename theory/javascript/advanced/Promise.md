A Promise is an object which represents eventual completion or failure of an asynchronous operation.

Promises are immutable once resolved and they give us a lot of control over our code.

They have three states
- **Pending:** Initial state, neither fulfilled nor rejected.
- **Fulfilled:** The operation completed successfully.
- **Rejected:** The operation failed.

The promise object contains two parts
1) Promise State (stores the sate of the promise)
2) Promise Result (stores data)

The state transitions are one-way: from pending to either fulfilled or rejected.

Once a Promise is settled (fulfilled or rejected), it cannot transition to any other state. This immutability ensures predictability in handling asynchronous operations.

---
### Anatomy of a Promise

**Promise Constructor**
The Promise object is created using the Promise constructor which takes a function called the executor
This executor function is executed immediately by the Promise implementation, passing resolve and reject functions (the executor is run synchronously)

```js
const myPromise = new Promise((resolve, reject) => {
  // asynchronous operation here
});
```

**Executor Function**
The executor function contains the logic of your asynchronous operation. It typically starts some asynchronous work, and then either calls resolve if the operation is successful or reject if it fails

```js
const myPromise = new Promise((resolve, reject) => {
  let success = true; // Example condition
  if (success) {
    resolve('Operation succeeded!');
  } else {
    reject('Operation failed.');
  }
});
```

---
### Creating and Using Promises

Let’s explore a practical example where we create a Promise that simulates an asynchronous operation, such as fetching data from a server

```js
const fetchData = new Promise((resolve, reject) => {
  // Simulate an asynchronous operation using setTimeout
  setTimeout(() => {
    const data = { id: 1, name: 'John Doe' }; // Sample data
    resolve(data); // Resolve the promise with data
  }, 2000); // 2-second delay
});

fetchData
  .then((data) => {
    console.log('Data received:', data);
  })
  .catch((error) => {
    console.error('Error:', error);
  });
```
### Chaining Promises

This allows for handling multiple asynchronous operations in sequence, ensuring each operation waits for the previous one to complete

Consider the following example, where we perform a series of operations that depend on each other

```js
const firstPromise = new Promise((resolve) => {
  setTimeout(() => resolve(1), 1000);
});

firstPromise
  .then((result) => {
    console.log(result); // 1
    return result * 2; // Pass result to next then
  })
  .then((result) => {
    console.log(result); // 2
    return result * 3; // Pass result to next then
  })
  .then((result) => {
    console.log(result); // 6
  })
  .catch((error) => {
    console.error('Error:', error);
  });
```
### Handling Errors in Promise Chains

If any of the then handlers throw an error or a Promise is rejected, the control jumps to the nearest catch handler

```js
const failingPromise = new Promise((resolve, reject) => {
  setTimeout(() => reject(new Error('Something went wrong!')), 1000);
});

failingPromise
  .then((result) => {
    console.log(result); // This will not run
  })
  .catch((error) => {
    console.error('Caught an error:', error);
  });
```

You can also handle errors within a then handler and continue the chain with a recovered value

```js
const recoverablePromise = new Promise((resolve, reject) => {
  setTimeout(() => reject(new Error('Initial failure')), 1000);
});

recoverablePromise
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.error('Error:', error);
    return 'Recovered from error'; // Recover from error
  })
  .then((result) => {
    console.log(result); // 'Recovered from error'
  });
```

---
### Promise States and State Transitions

A Promise can only change states once, from pending to either fulfilled or rejected.
This immutability makes sure that once a Promise is settled, its state and result cannot change.

```
Pending
  |
  +---> Fulfilled
  |
  +---> Rejected
```

### Practical Examples

Fetching Data

```js
function fetchData(url) {
  return new Promise((resolve, reject) => {
    const xhr = new XMLHttpRequest();
    xhr.open('GET', url);
    xhr.onload = () => {
      if (xhr.status === 200) {
        resolve(JSON.parse(xhr.responseText));
      } else {
        reject(new Error(`Request failed with status ${xhr.status}`));
      }
    };
    xhr.onerror = () => reject(new Error('Network error'));
    xhr.send();
  });
}

fetchData('https://api.example.com/data')
  .then((data) => {
    console.log('Data received:', data);
  })
  .catch((error) => {
    console.error('Error fetching data:', error);
  });
```

### Promise APIs / Handling Multiple Promises
##### `Promise.all`

- Takes an array of Promises
- Returns a single Promise that resolves when all of the input Promises have resolved
- If any of the input Promises reject, the resulting Promise will reject with the reason of the first Promise that rejects.

In this example, all Promises are resolved, so the then method receives an array of their values. If any of the Promises had rejected, the catch method would handle the error.

```js
const promise1 = Promise.resolve(3);
const promise2 = 42;
const promise3 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, 'foo');
});

Promise.all([promise1, promise2, promise3])
  .then((values) => {
    console.log(values); // [3, 42, "foo"]
  })
  .catch((error) => {
    console.error(error);
  });

// All success
// [3, 42, "foo"]

// promise3 failes
// foo
```
##### `Promise.race`

- Takes an array of Promises
- Returns a Promise that resolves or rejects as soon as one of the Promises in the array resolves or rejects.

This is useful when you need the result of the first completed Promise

In this case, `Promise.race` resolves with the value of promise2 because it completes first

```js
const promise1 = new Promise((resolve, reject) => {
  setTimeout(resolve, 500, 'one');
});
const promise2 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, 'two');
});

Promise.race([promise1, promise2]).then((value) => {
  console.log(value); // "two"
});

// The first finisher succeed
// two

// The first finisher fails
// two
```
##### `Promise.allSettled`

- Takes an array of Promises
- Waits for all Promises to be settled, meaning they have either resolved or rejected.
- Returns a Promise that resolves with an array of the results, each result being an object with a status property and a value or reason property

This example shows how `Promise.allSettled` provides a way to handle both resolved and rejected Promises without short-circuiting like `Promise.all`

```js
const promise1 = Promise.resolve('success');
const promise2 = Promise.reject('error');
const promise3 = new Promise((resolve) => setTimeout(resolve, 100, 'another success'));

Promise.allSettled([promise1, promise2, promise3]).then((results) =>
  results.forEach((result) => console.log(result.status))
);
// "fulfilled"
// "rejected"
// "fulfilled"
```
##### `Promise.any`

- Takes an array of Promises
- Returns a single Promise that resolves as soon as any of the input Promises resolve
- If none of the input Promises resolve (if all of them reject), it returns a Promise that rejects with an `AggregateError`, which is a new error type that groups together individual errors

In this example, `Promise.any` resolves with the value of the first fulfilled Promise (promise2), even though one of the Promises rejects.

```js
const promise1 = new Promise((resolve, reject) => {
  setTimeout(reject, 500, 'one');
});
const promise2 = new Promise((resolve) => {
  setTimeout(resolve, 100, 'two');
});
const promise3 = new Promise((resolve) => {
  setTimeout(resolve, 200, 'three');
});

Promise.any([promise1, promise2, promise3])
  .then((value) => {
    console.log(value); // "two"
  })
  .catch((error) => {
    console.error(error);
  });
```

---
### Avoiding Call back Hell

Call back hell, also known as “pyramid of doom,” occurs when call backs are nested within other call backs, leading to code that is hard to read and maintain

Without Promises (Call back Hell)

```js
doSomething(function (result) {
  doSomethingElse(result, function (newResult) {
    doThirdThing(newResult, function (finalResult) {
      console.log('Got the final result: ' + finalResult);
    });
  });
});
```

With Promises

```js
doSomething()
  .then((result) => {
    return doSomethingElse(result);
  })
  .then((newResult) => {
    return doThirdThing(newResult);
  })
  .then((finalResult) => {
    console.log('Got the final result: ' + finalResult);
  })
  .catch((error) => {
    console.error('Error occurred:', error);
  });
```

##### Sequential and Parallel Execution

Sequential

```js
doTask1()
  .then((result1) => {
    return doTask2(result1);
  })
  .then((result2) => {
    return doTask3(result2);
  })
  .then((finalResult) => {
    console.log('All tasks completed:', finalResult);
  })
  .catch((error) => {
    console.error('Error occurred:', error);
  });
```

Parallel

```js
doTask1()
  .then((result1) => {
    return doTask2(result1);
  })
  .then((result2) => {
    return doTask3(result2);
  })
  .then((finalResult) => {
    console.log('All tasks completed:', finalResult);
  })
  .catch((error) => {
    console.error('Error occurred:', error);
  });
```

---
### Using Promise Utilities

JavaScript provides utility functions for working with Promises, which can simplify handling complex asynchronous workflows
##### Timeout with Promises
You can create a timeout function that returns a Promise, which resolves after a specified delay
This delay function can be useful for creating delays between asynchronous tasks

```js
function delay(ms) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}

delay(2000)
  .then(() => {
    console.log('Executed after 2 seconds');
  });
```
##### Retrying with Promises
Sometimes, you may need to retry an asynchronous operation if it fails. You can create a utility function to handle retries with Promises

```js
function retryPromise(fn, retries) {
  return fn().catch((error) => {
    if (retries > 0) {
      console.log(`Retrying... (${retries} attempts left)`);
      return retryPromise(fn, retries - 1);
    } else {
      return Promise.reject(error);
    }
  });
}
```

In this example, `retryPromise` retries the `fetchData` function up to three times if it fails, providing a simple way to handle transient errors.

```js
function fetchData() {
  return new Promise((resolve, reject) => {
    // Simulate an asynchronous operation that may fail
    const success = Math.random() > 0.5;
    setTimeout(() => {
      success ? resolve('Data fetched successfully') : reject('Fetch failed');
    }, 1000);
  });
}

retryPromise(fetchData, 3)
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.error('All retries failed:', error);
  });
```

---
### Best Practices for Handling Asynchronous Operations

##### Using catch for Error Handling
Every Promise chain should have a catch method at the end to handle any errors that may occur in any of the then handlers.

If an error is thrown within a then handler or if a Promise is rejected, the catch method will be called with the error. This makes sure that the errors are not silently ignored and can be properly handled

```js
myPromise
  .then((result) => {
    // Do something with the result
  })
  .catch((error) => {
    console.error('Error occurred:', error);
  });
```

##### Using finally for Clean-up
The finally method allows you to run clean-up code regardless of whether the Promise was resolved or rejected. This can be useful for releasing resources or performing other clean-up tasks

In this example, the finally block runs regardless of whether the Promise was fulfilled or rejected, allowing for consistent clean-up

```js
myPromise
  .then((result) => {
    // Do something with the result
  })
  .catch((error) => {
    console.error('Error occurred:', error);
  })
  .finally(() => {
    console.log('Operation completed, cleaning up');
  });
```
##### Using Async/Await
They allow you to write asynchronous code that looks and behaves like synchronous code

Without async/await

```js
fetchData()
  .then((data) => {
    return processData(data);
  })
  .then((processedData) => {
    return saveData(processedData);
  })
  .then(() => {
    console.log('Data saved successfully');
  })
  .catch((error) => {
    console.error('Error occurred:', error);
  });
```

With async/await

```js
async function handleData() {
  try {
    const data = await fetchData();
    const processedData = await processData(data);
    await saveData(processedData);
    console.log('Data saved successfully');
  } catch (error) {
    console.error('Error occurred:', error);
  }
}

handleData();
```

##### Avoiding Unnecessary Promises
Avoid wrapping synchronous code in Promises unnecessarily.
If a function is already returning a Promise, there’s no need to wrap it again.
Wrapping synchronous operations in a Promise can add unnecessary complexity and degrade performance

Bad Practice

```js
function badPractice() {
  return new Promise((resolve, reject) => {
    try {
      let result = synchronousFunction();
      resolve(result);
    } catch (error) {
      reject(error);
    }
  });
}
```

Good practice

```js
function goodPractice() {
  try {
    let result = synchronousFunction();
    return Promise.resolve(result);
  } catch (error) {
    return Promise.reject(error);
  }
}
```
##### Combining Promises with Async/Await
You can combine Promises with async and await to handle multiple asynchronous operations more effectively

When you need to wait for multiple Promises to resolve, you can use Promise.all in combination with async/await to handle them concurrently

```js
async function fetchData() {
  try {
    const [response1, response2] = await Promise.all([
      fetch('https://api.example.com/data1'),
      fetch('https://api.example.com/data2')
    ]);
    const data1 = await response1.json();
    const data2 = await response2.json();
    console.log(data1, data2);
  } catch (error) {
    console.error('Error fetching data:', error);
  }
}

fetchData();
```
##### Avoiding Nested Promises
Nesting Promises can lead to code that is hard to read and maintain. Instead, chain Promises or use async/await to flatten the structure

Bad practice

```js
doSomething()
  .then((result) => {
    doSomethingElse(result)
      .then((newResult) => {
        doThirdThing(newResult)
          .then((finalResult) => {
            console.log('Got the final result: ' + finalResult);
          })
          .catch((error) => {
            console.error('Error in doThirdThing:', error);
          });
      })
      .catch((error) => {
        console.error('Error in doSomethingElse:', error);
      });
  })
  .catch((error) => {
    console.error('Error in doSomething:', error);
  });
```

Good practice - chaining

```js
doSomething()
  .then((result) => {
    return doSomethingElse(result);
  })
  .then((newResult) => {
    return doThirdThing(newResult);
  })
  .then((finalResult) => {
    console.log('Got the final result: ' + finalResult);
  })
  .catch((error) => {
    console.error('Error occurred:', error);
  });

// or using async / await

async function performTasks() {
  try {
    const result = await doSomething();
    const newResult = await doSomethingElse(result);
    const finalResult = await doThirdThing(newResult);
    console.log('Got the final result: ' + finalResult);
  } catch (error) {
    console.error('Error occurred:', error);
  }
}

performTasks();
```
##### Graceful Degradation and Fallbacks

Using Default Values
Provide default values in case an asynchronous operation fails

```js
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error fetching data:', error);
    return { default: 'Default data' }; // Fallback value
  }
}

fetchData().then((data) => {
  console.log(data);
});
```

Implementing Retries
Retry mechanisms can help handle transient errors by attempting the operation multiple times before failing

In this example, `fetchDataWithRetry` attempts to fetch data up to three times before failing, providing a simple way to handle transient errors

```js
async function fetchDataWithRetry(url, retries = 3) {
  for (let i = 0; i < retries; i++) {
    try {
      const response = await fetch(url);
      if (!response.ok) throw new Error('Network response was not ok');
      const data = await response.json();
      return data;
    } catch (error) {
      if (i === retries - 1) {
        console.error('All retries failed:', error);
        throw error;
      }
      console.log(`Retrying... (${i + 1}/${retries})`);
    }
  }
}

fetchDataWithRetry('https://api.example.com/data')
  .then((data) => {
    console.log('Data received:', data);
  })
  .catch((error) => {
    console.error('Failed to fetch data:', error);
  });
```

*Taken from [This Blog](https://medium.com/@AlexanderObregon/understanding-javascript-promises-b465719f9835)*










