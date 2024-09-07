An object is an unordered collection of key-value pairs. The key must either be a string or symbol data type where as the value can be of any data type

To retrieve a value, you can use the the corresponding key. This can be achieved using the dot notation or bracket notation

An object is not an iterable. You cannot use it with a `for...of` loop

```js
const obj = {
    name: 'vishal',
    age: 28,
    'key-three': true,
    sayMyName: function(){
        console.log(this.name)
    }
}
```

```js
// access
obj.name
obj['name']

// bracket notation is useful when key contains spaces or hyphen -
obj['key-three']

// adding a new property
obj.hobby = 'playing guitar'

// deleting a property
delete obj.hobby

// accessing methods
obj.sayMyName()
```

Other Methods
`Object.keys`, `Object .values` `Object.entries`

### Object - Big-O time complexity

Insert - O(1)
Remove - O(1)
Access - O(1)
Search - O(n)
`Object.keys()` O(n)
`Object.values()` - O(n)
`Object.entries()` - O(n)

