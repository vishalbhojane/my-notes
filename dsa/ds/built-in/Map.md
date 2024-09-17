A map is an unordered collection of key-value pairs. Both keys and values can be of any data type
To retrieve a value, you can use the the corresponding key
Maps are iterables. They can be used with a for of loop

### Object vs Map

Objects are unordered whereas **maps are ordered**

Keys in objects can only be string or symbol type whereas in maps, they can be of any type

An object has a prototype and may contain a few default keys which may collide with your own keys if you're not careful. A map on the other hand does not contain any keys by default

Objects are not iterables where as maps are iterables

The number of items in an object must be determined manually where as it is readily available with the `size` property in a map

Apart from storing data, you can attach functionality to an object whereas **maps are restricted to just storing data**

```js
const map = new Map([['a', 1],['b', 2]]) // a is key 1 is value...
```

Loop over 

```js
for(const [key,value] of map){
    console.log(key, value)
}
```

```js
// get value
map.get('a')

// add new value
map.set('c', 3)

// check if value exists
map.has('a')

// delete key
map.delete('c')

// size
map.size

// delete all keys
map.clear()
```

