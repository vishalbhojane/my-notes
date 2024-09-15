Throttling limits the execution of your code to once in every specified time interval

```js
function throttle(fn, delay) {
    let isTimerActive = false

    return function (...args) {
	    const context = this;
	    
        if (!isTimerActive) {
            fn.call(context, ...args)
            isTimerActive = true

            setTimeout(function () {
                isTimerActive = false
            }, delay)
        }
    }
}
```

Implementation using `Date()`

```js
function throttle(fn, delay) {
    let lastEventTime = 0
    
    return function (...args) {
        const currentEventTime = new Date().getTime()
        const context = this;

        if (currentEventTime - lastEventTime > delay) {
            fn.call(context, ...args)
            lastEventTime = currentEventTime
        }
    }
}
```

Simple Usage

```js
const logClick = () => console.log('click')
const throttledLogClick = throttle(logClick, 1000)

document.body.addEventListener('click', throttledLogClick)
```

With Arguments

```js
const logClick = (name) => console.log('click ' + name)
const debouncedLogClick = debounce(logClick, 1000)

document.body.addEventListener('click', () => { debouncedLogClick('vishal') })
```

Object Method

```js
// using regular function, because arrow function don't have their own 'this'
// they return the value of 'this' where they are written
function logClick() {
    console.log('click ' + this.fullName)
}

const person = {
    fullName: 'vishal',
    sayName: throttle(logClick, 1000)
}

const throttledLogClick = person.sayName.bind(person)
// document.body.addEventListener('click', () => { throttledLogClick('vishal') })

// or 

document.body.addEventListener('click', () => { person.sayName() })
```

Advanced throttling function (Kyle Cook)

```js
function throttle(callback, delay = 1000) {
    let shouldWait = false
    let waitingArgs;
    const timeoutFn = (...args) => {
        if (waitingArgs == null) {
            shouldWait = false;
        } else {
            callback(...waitingArgs);
            waitingArgs = null;
            setTimeout(timeoutFn, delay)
        }
    }
    return (...args) => {
        if (shouldWait) {
            waitingArgs = args
            return
        }
        callback(...args);
        shouldWait = true;
        setTimeout(timeoutFn, delay)
    }
}
```

#### Analogy
Baby: Mom give me a piece of chocolate cake
Mom: No you can get one, only after 1 hour
(baby wont get a piece of cake no matter how many times she asked, but only after each hour)
