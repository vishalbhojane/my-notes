Calling `event.preventDefault() `during any stage of event-flow cancels the event
meaning that any default action normally taken by the implementation as a result of the event will not occur.


Calling` preventDefault()` for a non-cancellable event has no effect.
You can use `event.cancelable` to check if the event is cancellable.

```js
form.addEventListener("submit", e => {
    e.preventDefault() // prevent window refrest when submitting a form
    console.log("submitted form");
});
```

more ex

```js
const link = document.querySelector("a");
link.addEventListener("click", e => { // click, mouseenter, mouseleave, mouseover, focus, blur
    e.preventDefault()
    console.log("Prevented Default");
});

window.addEventListener("resize", () => console.log("resize"));
```