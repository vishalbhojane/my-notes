#### Before
iteration in javascript

```js
// for string
const str = "vishal"
for (let i = 0; i < str.langth; i++) {
    const c = str.charAt(i)
}

// for array
const arr = ['apple', 'banana', 'watermelon']
for (let i = 0; i < arr.length; i++) {
    const el = arr[i]
}
```

in above code
- Difficulty in accessing the elements
- Difficult to manage iteration on the data for various data structure

#### Now
JavaScript provides a protocol to iterate over data structures.
This protocol defines how these data structures are iterated over using the for...of loop.

The concept of the protocol can be split into:
- **iterable** - The data structures that have the Symbol.iterator() method are called iterables. For example, Arrays, Strings, Sets, etc
- **iterator** - An iterator is an object that is returned by the Symbol.iterator() method

```js
const arr = [1, 2 ,3];

// calling the Symbol.iterator() method
const arrIterator = arr[Symbol.iterator]();

// gives Array Iterator
console.log(arrIterator);
// Array Iterator {}
```

```js
const str = 'hello';

// calling the Symbol.iterator() method
const strIterator = str[Symbol.iterator]();

// gives String Iterator
console.log(strIterator);
// StringIterator {}
```

Iterate Through Iterables

```js
const number = [ 1, 2, 3];
for (let n of  number[Symbol.iterator]()) {
    console.log(n);
}
```

Or you can simply iterate through the array like this:

```js
for (let n of  number) {
    console.log(n);
}
```

## `next()` Method
The iterator object has a next() method that returns the next item in the sequence.

The next() method contains two properties: value and done.
- **value** - The value property can be of any data type and represents the current value in the sequence.
- **done** - The done property is a boolean value that indicates whether the iteration is complete or not. If the iteration is incomplete, the done property is set to false, else it is set to true

```js
const arr2 = ['h', 'e', 'l', 'l', 'o'];
const arrIterator2 = arr[Symbol.iterator]();

console.log(arrIterator2.next()); // {value: "h", done: false}
console.log(arrIterator2.next()); // {value: "e", done: false}
console.log(arrIterator2.next()); // {value: "l", done: false}
console.log(arrIterator2.next()); // {value: "l", done: false}
console.log(arrIterator2.next()); // {value: "o", done: false}
console.log(arrIterator2.next()); // {value: undefined, done: true}
```

### custom iterable

```js
const obj = {
    [Symbol.iterator]: function () {
        let step = 0;
        const iterator = {
            next: function () {
                step++

                if (step === 1) {
                    return { value: 'Hello', done: false }
                } else if (step === 2) {
                    return { value: 'World', done: false }
                }
                return { value: undefined, done: true }
            }
        }
        return iterator
    }
}

for(let word of obj){
    console.log(word)
}
```

we have created our custon iterable '`obj`'
just like we did above, javascript intenally does for Strings, Arrays, Maps and Sets

### custom iterator using generator function

```js
function* generatorFunction(){
    yield "hello"
    yield "world"
}

const generatorObject = generatorFunction()

for (let word of generatorObject){
    console.log(word.next().value)
}
```