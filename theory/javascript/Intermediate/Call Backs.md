callback is a function that passed to another function in order to be executed at a later time based on some specific condition

callbacks are way to do the asychronus task in javascript

```js
console.log('namaste');

setTimeout(function () { // callback - executed later
    console.log('javascript');
});

console.log('season 2');

// namaste
// season 2
// javascript
```

more ex

```js
const cart = ['phone', 'shoes', 'watch']

api.createOrder(data, function () {
    api.proceedToPayment(function () {
        api.showOrderSummery(function () {
            api.updateWallet()
        })
    })
})
```

## Two issues while using call-backs

#### 1. Callback hell
When a function is passed as an argument to another function, it becomes a callback function.
This process continues and there are many callbacks inside another's Callback function.
This grows the code horizontally instead of vertically. That mechanism is known as callback hell.

#### 2. Inversion of control
The callback function is passed to another callback, this way we lose the control of our code.
We don't know what is happening behind the scene and the program becomes very difficult to maintain.
That process is called inversion of control. 