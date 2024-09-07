An array is a data structure that can hold a collection of values

Arrays can contain a mix of different data types. You can store `strings`, `booleans`, `numbers` or even `objects` all in the same array

Arrays are resizable. You don't have to declare the size of an array before creating it

JavaScript arrays are zero-indexed and the insertion order is maintained

Arrays are iterables. They can be used with a `for...of` loop

```js
const arr = [1,2,3,4]
```

First Element

```js
arr[0]
```

Last element

```js
arr[arr.length - 1]
```

Methods

```js
arr.push(5)     // add at the end
arr.pop()       // remove from the end
arr.unshift(5)  // add at the begining
arr.shift()     // remove from the begining
```

Loop over array

```js
for(const item of arr){
    console.log(item)
}
```

Other Methods
`map`, `filter`, `reduce`, `concat`, `slice`, `splice`

#### Array - Big-O time complexity

Insert / remove from end - O(1)
Insert/remove from beginning - O(n)
Access - O(1)
Search - O(n)
`push`/`pop` - O(1)
`shift` / `unshift`/`concat` / `slice` / `splice` - O(n)
`forEach`/`map`/`filter`/ `reduce` - O(n)