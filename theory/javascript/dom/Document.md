a `document` is an object that gives access to and manipulates the currently loaded HTML document.
It is a part of the `window` global object, which represents the window of the current web page.

to get HTML portion of document

```js
document.documentElement
```

to get body

```js
document.body
```

creating span element

```js
const element = document.createElement("span");
```

```js
element.innerText = "helloWorld"
document.body.appendChild(element) // adds 'hello world' at the end of he body
```

grab one single element based on its id.
id is suppose to be unique on the page.
if we pass the id that doesn't exists. then it returns null

```js
const divWithId = document.getElementById("div-id");
```

Setting inline `css`

```js
divWithId.style.color = "red";
```

grabbing array of elements that matches the class name. because classes can be on ton of elements

```js
const divsWithClass = document.getElementsByClassName("div-class");
```

creating array from above HTML collection

```js
const divsWithClassArray = Array.from(divsWithClass);
```

to style single element

```js
divsWithClass[0].style.color = "yellow"
```

`querrySelector()`
we can select an element using `css` selector "#id .class element"
returns first matching element

to select data attribute element

```js
document.querySelector('[data-test]')
```

input element

```js
document.querySelector("input")
```

to be more explicit, selecting text type

```js
document.querySelector("input [type='text']")
```

to be moe explicit, select inside body

```js
document.querySelector("body > input [type='text']")
```

`querySelectorAll()`
returns all matching element
returns node list of it, similar to array

```js
const divsWithClasses = document.querySelectorAll('.div-class');
```

node list has `forEach()` method. to use all array method we need to convert it to array first

```js
divsWithClass.forEach(div => (div.style.color = "red"))
```