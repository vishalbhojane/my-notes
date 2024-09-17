An event listener is a function in JavaScript that waits for an event to occur then responds to it.

```js
const btn = document.querySelector(".btn");
```

Adding an event listener

```js
btn.addEventListener('click', () => {
    console.log("clicked from 1st listener")
})

btn.addEventListener('click', () => {
    console.log("clicked fronm 2nd listener")
})
```

Above both will work in the order they are added, they will not overwrite each other

Removing an event listener

```js
function printClick() {
    console.log("Clicked")
}
btn.removeEventListener("click", printClick);
```

Event Object - comes with lot of properties and methods

```js
btn.addEventListener("click", event => {
    console.log(event);
})
```

Input events

```js
const input = document.querySelector("[data-input-text]");
input.addEventListener("change", () => {
    // logs when input is changed..we go off the text box in this case (key to mouse)
    console.log(change)
})

input.addEventListener("input", () => {
    // logs all input activity. type, delete..etc
    console.log(input)
})

input.addEventListener("input", e => {
    // returns true if the input is emty string i.e. nothing inside input box 
    console.log(e.target.value === "")
})
```

Form events

```js
const form = document.querySelector("[data-form]")

form.addEventListener("submit", e => {
    // it flashes in console and runs away (because, page refreshes after form submit)
    console.log("submitted form")
});
```