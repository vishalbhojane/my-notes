The Document Object Model (DOM)
it is the data representation of the objects that comprise the structure and content of a document on the web.

Window Object - global object for the entire browser

```js
console.log(window);
```

console is also a part of window. above is same as saying

```js
window.console.log()
```

case when writing window makes sense

```js
window.addEventListener('resize', () => {
    console.log('resized')
});
```