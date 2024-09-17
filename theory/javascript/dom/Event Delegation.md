*Event Delegation is basically a pattern to handle events efficiently.*

Instead of adding an event listener to each and every similar element,
we can add an event listener to a parent element and call an event on a particular target using the .target property of the event object.

```html
<div>
    <ul id="category">
        <li id="laptops">laptops</li>
        <li id="cameras">cameras</li>
        <li id="shoes">shoes</li>
    </ul>
</div>
```

```js
document.querySelector("#category").addEventListener('click', (e) => {
    console.log(e.target);
    if (e.target.tagName == 'LI') {
        window.location.href = "/" + e.target.id;
    }
});
```

```html
<div id="form">
    <input type="text" id="name" data-uppercase>
    <input type="text" id="pan">
    <input type="text" id="mobile" data-uppercase>
</div>
```

```js
document.querySelector("#form").addEventListener('keyup', (e) => {
    console.log(e);
    if (e.target.dataset.uppercase != undefined) {
        e.target.value = e.target.value.toUpperCase();
    }
})
```

### Benefits
saves memory by attaching less event handlers
writing less code
`dom` manipulation - tough to add event listener to newly added child (eg. in infinite scroll we keep adding new child)

### Cons
all events are not bubbled up: blur, focus, scroll