### Call back Queue

stores functions that have been passed as arguments to asynchronous functions such as `setTimeout()`
These functions are executed only after the Call Stack is empty, meaning all synchronous functions have finished execution

### Microtask Queue

used to store asynchronous operations that require immediate execution compared to regular call back functions

---
### Difference between call back and microtask queue

| Call back Queue                                                                                                   | Microtask Queue                                                                                             |
| ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Call back Queue gets the ordinary call back functions coming from the `setTimeout()` API after the timer expires. | Microtask Queue gets the callback functions coming through Promises and Mutation Observer.                  |
| Call back Queue has lesser priority than Microtask Queue of fetching the call back functions to Event Loop.       | Microtask Queue has higher priority than Call back Queue of fetching the call back functions to Event Loop. |
