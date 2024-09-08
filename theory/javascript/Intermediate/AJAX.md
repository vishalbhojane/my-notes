Asynchronous JavaScript is a programming approach that enables the non-blocking execution of tasks, allowing concurrent operations, improved responsiveness, and efficient handling of time-consuming operations in web applications,

JavaScript is a single-threaded and synchronous language. The code is executed in order one at a time,
But Javascript may appear to be asynchronous in some situations

There are several methods that can be used to perform asynchronous javascript tasks, which are listed below
- Using call-backs
- Using Promises

```js
setTimeout(
    () => { console.log("inside") } // callback
    , 1000)
console.log("outside")

const button = document.querySelector("#asy")
button.addEventListener("click", () => { // callback after click event
    console.log("clicked")
})
```