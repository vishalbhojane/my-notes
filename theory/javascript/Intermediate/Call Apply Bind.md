These methods helps you change the context of the invoking function.
it is use replace the value of 'this' inside a function with whatever value you want.

## `call()`
We can use 'call' to borrow methods / functions

```js
let person1 = {
    firstName: 'vishal',
    lastName: 'bhojane',
    printFullName: function () {
        console.log(this.firstName + " " + this.lastName)
    }
}
let person2 = {
    firstName: 'ankesh',
    lastName: 'bhojane',
}
```

borrow method from other object

```js
person1.printFullName.call(person2); // Method borrowed from person1
```

change context of standalone function

```js
function printFullName2() {
    console.log(this.firstName + " " + this.lastName)
}
printFullName2.call(person2);
```

we can also pass the arguments to 'call' method

```js
function printFullNameAndHometown(hometown) {
    console.log(this.firstName + " " + this.lastName + " from" + hometown)
}
printFullNameAndHometown.call(person2, 'mumbai')
```

Multiple arguments (pass them comma seperated)

```js
function printFullNameAndHometownAndState(hometown, state) {
    console.log(this.firstName + " " + this.lastName + " from " + hometown + ", " + state)
}
printFullNameAndHometownAndState.call(person2, 'mumbai', 'maharashtra')
```

## `apply()`
same as call method, only difference is that we pass the arguments as a array

```js
printFullNameAndHometownAndState.apply(person2, ['mumbai', 'maharashtra'])
```

## `bind()`
same as call, but with one difference
it does not invoke the method directly, instead it returns the function, which can be invoked later

```js
let printDetails = printFullNameAndHometownAndState.bind(person2, 'mumbai', 'maharashtra');
printDetails()
```