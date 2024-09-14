*Functions that calls itself*
Recursion is used to solve problems that contain smaller sub-problems

```js
function printHi() {
    printHi()
}
```

Print numbers from 1 to 10

```js
function printNumber(number) {
    if (number > 10) return // exit condition

    console.log(number)

    printNumber(number + 1) // recursive call
}
printNumber(1) // start number
```

Sum numbers below

```js
function sumNumbersBelow(number) {
    if (number <= 0) return 0 // exit condition
    return number + sumNumbersBelow(number - 1)
}
const result = sumNumbersBelow(10);
```

More ex

```js
const person = {
    name: "kyle",
    friend: {
        name: "joe",
        friend: {
            name: "sally"
        }
    }

}
function printNames(currentPerson) {
    if (currentPerson === null) return
    console.log(currentPerson.name)
    printNames(currentPerson.friend)
}
printNames(person)
```