Event bubbling and capturing are two ways of event propagation in the HTML DOM API

when an event occurs in an element inside another element, and both elements have registered a handle for that event.
The event propagation mode determines in which order the elements receive the event.

**Bubbling**: the event is first captured and handled by the innermost element and then propagated to outer elements.
**Capturing**: the event is first captured by the outermost element and propagated to the inner elements.

Capturing is also called "trickling", which helps remember the propagation order:
*Trickle down, Bubble up*

#### Stopping bubbling
The method for it is `event.stopPropagation()`

#### Capture is off by default
to enable, set this in add event listener `{capture: true}`

```html
< div id="grandparent" >
    <div id="parent">
        <div id="child"></div>
    </div>
</div >
```

```js
document.querySelector("#grandparent")
    .addEventListener('click', (e) => {
        console.log("Grandparent Clicked!");
        // e.stopPropagation();
    }, { capture: true });

document.querySelector("#parent")
    .addEventListener('click', (e) => {
        console.log("Parent Clicked!");
    },);

document.querySelector("#child")
    .addEventListener('click', (e) => {
        console.log("Child Clicked!");
    },);
```