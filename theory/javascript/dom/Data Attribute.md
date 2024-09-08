The `data-*` attributes is used to store custom data private to the page or application.

```html
<element data-*="somevalue">
```

to get all the data attribute on element with 'test' data attribute

```js
const test = document.querySelector(['[data-test]']); // 1. select elememt
console.log(test.dataset) // 2. returns object with - is replaced and with camelCase
```

to access individual properties

```js
console.log(test.dataset.test)
console.log(test.dataset.testTwo)
```

to set values

```js
test.dataset.test = "5555"
```

use case

```js
const buttons = document.querySelectorAll("button");
buttons.forEach(button => {
    button.addEventListener("click", () => {
        const currentClicks = button.dataset.clicks ? button.dataset.clicks : 0
        button.dataset.clicks = parseInt(currentClicks) + 1
    })
})
```