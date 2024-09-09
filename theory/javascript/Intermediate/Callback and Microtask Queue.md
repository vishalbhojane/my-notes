### Callback Queue
stores functions that have been passed as arguments to asynchronous functions such as `setTimeout()`
These functions are executed only after the Call Stack is empty, meaning all synchronous functions have finished execution

### Microtask Queue
used to store asynchronous operations that require immediate execution compared to regular callback functions

#### Difference between callback and microtask queue

| Callback Queue                                                                                                | Microtask Queue                                                                                           |
| ------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Callback Queue gets the ordinary callback functions coming from the setTimeout() API after the timer expires. | Microtask Queue gets the callback functions coming through Promises and Mutation Observer.                |
| Callback Queue has lesser priority than Microtask Queue of fetching the callback functions to Event Loop.     | Microtask Queue has higher priority than Callback Queue of fetching the callback functions to Event Loop. |
