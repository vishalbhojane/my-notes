DE bouncing delays the execution of your code until the user stops performing a certain action for a specified amount of time.

```js
function debounce(fn, delay) {
    let timeoutId;
    return function () {
        const context = this
        clearTimeout(timeoutId)
        timeoutId = setTimeout(function () {
            fn.call(context)
        }, delay)
    }
}
```

Simple Usage

```js
const logClick = () => console.log('click')
const debouncedLogClick = debounce(logClick, 1000)

document.body.addEventListener('click', debouncedLogClick)
```

With Arguments

```js
const logClick = (name) => console.log('click ' + name)
const debouncedLogClick = debounce(logClick, 1000)

document.body.addEventListener('click', () => { debouncedLogClick('vishal') })
```

Object Methods

```js
// using regular function here because, arrow function do not have their own 'this', they return the value of this where they are written
function logClick() {
    console.log('click ' + this.fullName)
}

const person = {
    fullName: 'vishal',
    sayName: debounce(logClick, 1000)
}

const debouncedLogClick = person.sayName.bind(person)
// document.body.addEventListener('click', () => { debouncedLogClick('vishal') })

// or 

document.body.addEventListener('click', () => { person.sayName() })
```

