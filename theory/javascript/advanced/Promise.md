A Promise is an object which represents eventual completion or failure of an asynchronous operation.

Promises are immutable once resolved and they give us a lot of control over our code.

They have three state pending, fulfilled or rejected.

The promise object contains two parts
1) Promise State (stores the sate of the promise)
2) Promise Result (stores data)

#### Creating a Promise

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

### Consuming a promise

```js
myPromise
    .then(value => {
        console.log(value)
    })
    .catch(error => {
        console.log(error)
    })
    .finally(() => {
        console.log('cleaning up')
    })
```

**Question**
here `proceedToPayment(orderId)` needs to be call after `createOrder(cart)`
`createOrder(cart);`
`proceedToPayment(orderId);`

```js
// 1. using callback
createOrder(cart, function (orderId) {
    proceedToPayment(orderId)
})

// 2. using promise
createOrder()
    .then(orderId => {
        proceedToPayment()
    })
```

#### Promise chaining (resolving call back hell)
Important: always return, when chaining the promises

Producer

```js
function createOrder(cart) {
    const pr = new Promise(function (resolve, reject) {
        if (!validateCart(cart)) { // checking the cart
            const err = new Error('Cart is not valid')
            reject(err)
        }
        // other logic for createOrder
        // ....
        const orderId = '12345'
        if (orderId) {
            resolve(orderId)
        }
    });
    return pr
}

function proceedToPayment(orderId) {
    return new Promise(function (resolve, reject) {
        resolve('payment successful', orderId)
    })
}
```

Consumer

```js
createOrder(cart)
    .then(function (orderId) {
        return proceedToPayment(orderId)
    })
    .then(function (paymentInfo) {
        return showOrderSummery(paymentInfo);
    })
    .then(function (paymentInfo) {
        return updateWalletBalance(paymentInfo)
    })
    .catch(function (error) { // catch the error
        console.log(error)
    })
    .finally(function () { // does not take any argument
        console.log('runs at the end')
    })
```


### Sequential Execution

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

### Parallel execution (see `Promise.all`)

## Promise APIs

Input

```js
const p1 = new Promise(function (resolve, reject) {
    setTimeout(() => { resolve('p1 success') }, 3000);
    // setTimeout(() => { reject('p1 fail') }, 3000);
})
const p2 = new Promise(function (resolve, reject) {
    setTimeout(() => { resolve('p2 success') }, 1000);
    // setTimeout(() => { reject('p2 fail') }, 1000);
})
const p3 = new Promise(function (resolve, reject) {
    setTimeout(() => { resolve('p3 success') }, 2000);
    // setTimeout(() => { reject('p3 fail') }, 2000);
})
```

#### `Promise.all()`
takes an iterable of promises as input and returns a single Promise
It will wait for all of them to finish.
As soon as any promise gets rejected, `Promise.all` will throw the same error received from the rejected promise. It will not wait for other promises to get successful/rejected

```js
const promise_all = Promise.all([p1, p2, p3]);

// all succeed
promise_all.then(res => console.log(res)).catch(err => console.log(err))
//  [ 'p1 success', 'p2 success', 'p3 success' ]

// one of the promises fails
// p2 fail
```

#### `Promise.allSetteled()`
takes an iterable of promises as input and returns a single Promise
wait for all promises to be completed (resolve or reject) and it will give us a result from all promises

```js
const promise_allSettled = Promise.allSettled([p1, p2, p3]);

// all succeed
// [
//     { status: 'fulfilled', value: 'p1 success' },
//     { status: 'fulfilled', value: 'p2 success' },
//     { status: 'fulfilled', value: 'p3 success' }
// ]

// one of the promises fails
// [
//     { status: 'fulfilled', value: 'p1 success' },
//     { status: 'rejected', reason: 'p2 fail' },
//     { status: 'fulfilled', value: 'p3 success' }
// ]
```

#### `Promise.race()`
takes an iterable of promises as input and returns a single Promise
This returned promise settles with the eventual state of the first promise that settles
the first finisher will be returned, it does not matter if it succeeds or is rejected

```js
const promise_race = Promise.race([p1, p2, p3]);

// The first finisher succeed (Will get result after 1 second (check p2 implementation))
// p2 success

// The first finisher gets rejected (Will get result after 1 second (check p2 implementation))
// p2 fail
```

#### `Promise.any()`
Similar to Promise.race but it will wait to get any first success result
It rejects when all of the input's promises are rejected (including when an empty iterable is passed)
returns an AggregateError containing an array of rejection reasons

```js
const promise_any = Promise.any([p1, p2, p3]);
promise_all.then(res => console.log(res)).catch(err => console.log(err.errors)) // important, we are logging err.errors

// first finisher succeed
// P2 Success (Will get result after 1 second (check p2 implementation))

// first finisher gets rejected
// P3 Succeed. (Will get result after 2second from p3 (p1 and p2 rejected))

// All Promise gets rejected
// AggregateError: All promises were rejected (in case or console.log(err))
// [ 'p1 fail', 'p2 fail', 'p3 fail' ] (in case or console.log(err.errors))
```

To-do
Update from here
[Medium](https://medium.com/@AlexanderObregon/understanding-javascript-promises-b465719f9835)

