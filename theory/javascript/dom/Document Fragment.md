A Document Fragment is a temporary container used to hold multiple nodes without affecting the current DOM tree.
It allows for efficient addition and modification of nodes without triggering frequent layout updates, leading to enhanced performance and lower resource consumption compared to direct DOM manipulation.
Document Fragments help minimize rendering delays when dealing with complex animation, interactivity, and data visualization use cases.

##### 1. Create a new document fragment instance:

```js
const frag = document.createDocumentFragment();
```

##### 2. Add content to the fragment using Node methods like `appendChild()`:

```js
const data = [0,1,2,3,4,5]
let item;
for (let i = 0; i < data.length; i++) {
    item = document.createElement('li');
    item.textContent = data[i];
    frag.appendChild(item);
}
targetElement.appendChild(frag);
```

##### 3. Insert the entire fragment directly into the target element instead of iterating through individual children:

```js
targetElement.appendChild(frag);
```