It coordinates different parts of JavaScript runtime such as the Call Stack, Callback Queue, and Web APIs.
Its primary goal is to ensure all events, both synchronous and asynchronous, are handled properly within a single threaded environment

the Event Loop follows three basic steps
A. Check the Call Stack
	If there are no functions left on the Call Stack, move to Step B
B. Check the Callback Queue & Web APIs (fetch)
	If either contains pending tasks, push them onto the Call Stack and run

```js
function test() {
    console.log(1)
    console.log(2)
    setTimeout(() => { console.log(3) }, 10);
    setTimeout(() => { console.log(4) }, 0);
    console.log(5)
}
test()
console.log(6)

// 1
// 2
// 5
// 6
// 4 - wont run until the stack is empty, i.e completing the execution of test()
// 3
```

main thread - all your code runs
setTimeout - creates seperate thread, then after the timeout it plugs back to main thread

more ex

```js
function test() {
    console.log(1)
    console.log(2)
    setTimeout(() => { console.log(4) }, 0);
    new Promise((resolve, reject) => resolve("hi promise")).then(message => console.log(message))
    setTimeout(() => { console.log(3) }, 10);
    console.log(5)
}

// 1
// 2
// 5
// hi promise - Promise ran before timeouts even it is written after setTimeout(), because promise does not wait until all the task is complete i.e emptying of call stack. it just waits till the curently running function is complete. So Promise (waits for current function to complete) is preferred over normal callback (callback waits till call stack is empty)
// 4 - wont run until the stack is empty, that is completing the execution of test()
// 3
```