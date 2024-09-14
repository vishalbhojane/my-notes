Call back is a function that passed to another function in order to be executed at a later time based on some specific condition

Call backs are way to do the asynchronous task in JavaScript

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

---
### Two issues while using call-backs

##### 1. Call back hell
When a function is passed as an argument to another function, it becomes a call back function.
This process continues and there are many call backs inside another's Call back function.
This grows the code horizontally instead of vertically. That mechanism is known as call back hell.
##### 2. Inversion of control
The call back function is passed to another call back, this way we lose the control of our code.
We don't know what is happening behind the scene and the program becomes very difficult to maintain.
That process is called inversion of control. 