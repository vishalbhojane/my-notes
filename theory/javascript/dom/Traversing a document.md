Traversing the DOM refers to the process of navigating through the different elements in an HTML document using JavaScript

to traverse the `document` we have we have `parentElement`, `children`, `nextElementSibling`, `previousElementSibling`
<div class="grandparent">
    <div class="parent">
        <div class="children"></div>
        <div class="children"></div>
    </div>
    <div class="parent">
        <div class="children"></div>
        <div class="children"></div>
    </div>
</div>

```js
const grandParentEl = document.querySelector('.grandparent');
const parentEl = document.querySelector('.parent');
const childrenEl = document.querySelector('.children'); //> Returns first matching .children

grandParentEl.children //> .parenet
grandParentEl.children[0] //> first .parent
grandParentEl.children[1] //> second .parent

grandParentEl.children[0].nextElementSibling //> alt way to get second .parent

childrenEl.parentElement //> to get .parent
parentEl.parentElement //> to get .grandparent

childrenEl.closest('.parent') //> to get immediate .parent
childrenEl.closest('.grandparent') //> to get immediate .grandparent
```

```js
grandParentEl.querySelectorAll(".children").forEach(el => el.style.color = 'red')
```