Stands for asynchronous JavaScript. Is a programming approach that enables the non-blocking execution of tasks, allowing concurrent operations, improved responsiveness, and efficient handling of time-consuming operations in web applications,

JavaScript is a single-threaded and synchronous language. The code is executed in order one at a time,
But JavaScript may appear to be asynchronous in some situations

There are several methods that can be used to perform asynchronous JavaScript tasks, which are listed below
- [[Call Backs]]
- [[notes/theory/javascript/advanced/Promise|Promise]]

```js
setTimeout(
	// callback function
	() => {
		console.log("inside")
	}
	, 1000)
```

```js
const button = document.querySelector("#asy")
button.addEventListener("click", () => { // callback after click event
	console.log("clicked")
})
```
