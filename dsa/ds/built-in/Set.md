A set is a data structure that can hold a collection of values. The values however must be unique

Set can contain a mix of different data types. You can store strings, booleans, numbers or even objects all in the same set
Sets are dynamically sized. You don't have to declare the size of a set before creating it
Sets do not maintain an insertion order
Sets are iterables. They can be used with a for of loop

### Set vs Array

Arrays can contain duplicate values whereas Sets cannot
Insertion order is maintained in arrays but it is not the case with sets
Searching and deleting an element in the set is faster compared to arrays

```js
const set = new Set([1,2,3])
```

Loop over

```js
for(const item of set){
    console.log(item)
}
```

```js
// adding new value
set.add(4)

// if u add duplicate value, set will ignore
set.add(4)

// check if the value exist
set.has(4)

// to delete the value
set.delete(4)

// to check size of the set
set.size

// to remove all the valuew
set.clear()
```