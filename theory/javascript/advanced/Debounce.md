DE bouncing delays the execution of your code until the user stops performing a certain action for a specified amount of time.

```js
function debounce(fn, delay) {
    let timeoutId;
    
    return function (...args) {
        const context = this
        
        clearTimeout(timeoutId)
        
        timeoutId = setTimeout(function () {
            fn.call(context, ...args)
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

Inside Object Method

```js
// using regular function, because arrow function don't have their own 'this'
// they return the value of 'this' where they are written
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

#### Analogy
Baby: Mom give me a piece of chocolate cake, . . .Mom give me a piece of chocolate cake... mom give me...
Mom: No, You will get a piece of cake only after 1 hour from LAST time you asked for one.

