Iterable is an object that defines the Iterator property.
In order to be iterable, an object must implement the `@@iterator` method.
The property `Symbol.Iterator` on an object converts the object into Iterable
Iterables which can iterate only once (such as Generators) customarily return `this` from their `@@iterator` method
Iterables which can be iterated many times must return a new iterator on each invocation of `@@iterator`

```js
var iterable ={
    [Symbol.iterator] : () => {
        //Iterator defination
    }
}
```

### Custom iterable

```js
var iterable = {
    "numbers": [1,2,3,4,5],
    [Symbol.iterator]: function(){
        var index = 0

        return {
            next: function(){ // can be replaced with arrow function, then just remove the 'bind'
                if(index < this.numbers.length){
                    var temp = {value: this.numbers[index], done: false}
                    index++
                    return temp
                } else {
                    return {value: undefined, done: true}
                }
            }.bind(this)
        }
    }
}

for(const i of iterable){
    console.log(i)
}
```
### Relation between Iterable and Iterator.

As discussed above Iterable is an object which consists of an Iterator
Iterator is defined under the key `Symbol.Iterator`.
Iterator is the action definition of iteration this holds the custom logic of next() function
Next function is called iteratively and as per the protocol it returns value and done keys.

![[iterable-iterator.webp]]

---
### Iterator

Iterators often used in combination with the `for...of` loop in JavaScript to iterate over elements in a simple and readable manner.

Built-in JavaScript functions and methods, such as `Array.prototype.map() or Array.prototype.forEach()`, to process collections internally use Iterators

_Long story short, iterator is a closure which returns an object having having function next()/ or function next(), on each subsequent calling of the next function we get the next iteration value_

### Building blocks of an Iterator

`next()`:  next function returns an object consisting of two keys {value , done}.

`{value , done}`: Each next execution returns a value but done is returned as false until the iteration is complete(reaches length of the array/ object). Once all the values are iterated the done is returned as true and value turns out to be undefined.

`Symbol.iterator`: This symbol is a well-known symbol in JavaScript that defines the default iterator for an object. It is typically implemented as a function that returns the iterator object itself

To use an iterator you typically call the `Symbol.iterator` method on a collection or data structure to obtain an iterator object

---
### Lets use an iterator over an array

```js
var temp = [1,2,3]

// 1. Fetch the iterator object for the collection or data structure(array in this case)
var iterator = temp[Symbol.iterator]

// 2. use .next() on the iterator to fetch the values:

iterator.next(); // returns { value: 1, done: false }

iterator.next(); // returns { value: 2, done: false }

iterator.next(); // returns{ value: 3, done: false }

iterator.next(); // returns { value: undefined, done: true }
```

---
### Custom Iterator

```js
var arr = [1,2,3,4,5]

Array.prototype.iterator = function(){
    var count = 0;

    return {
        next: function(){
            for(var i = count; i < this.length; i++){
                var res = {value: this[i], done: false}
                count++
                return res
            }
            return {value: undefined, done: true}
        }.bind(this)
    }
}

var itr = arr.iterator()

var i = itr.next()

while(!i.done){
    console.log(i)
    i = itr.next()
}

// to print the done true after all the items done executing
console.log(i)
```

Above code using generator

```js
var arr = [1,2,3,4,5]

Array.prototype.iterator = function* (){
    var count = 0;

    for(var i = count; i < this.length; i++){
        yield this[i]
        count++
    }
}

var itr = arr.iterator()

var i = itr.next()

while(!i.done){
    console.log(i)
    i = itr.next()
}

// to print the done true after all the items done executing
console.log(i)
```

iterators and iterables are fundamental concepts in JavaScript that facilitate the traversal and manipulation of collections.
Iterators provide a standardised way to access elements sequentially
Iterables are objects that define the iteration behaviour by implementing the iterator protocol

---
### Custom iterator using generator function

```js
function* generatorFunction(){
    yield "hello"
    yield "world"
}

const generatorObject = generatorFunction()

for (let word of generatorObject){
    console.log(word.next().value)
}