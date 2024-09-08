Throttling limits the execution of your code to once in every specified time interval

```js
function throttle(fn, delay) {
    let isTimerActive = false
    let context = this;
    
    return function (...args) {
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
    let lastEventTime = 0;
    return function (...args) {
        let currentEventTime = new Date().getTime()
        if (currentEventTime - lastEventTime < delay) return
        lastEventTime = currentEventTime
        fn(...args)
    }
}
```

Simple Usage

```js
const logClick = () => console.log('click')
const throttledLogClick = throttle(logClick, 1000)

document.body.addEventListener('click', throttledLogClick)
```

Object Method

```js
// using regular function here because, arrow function do not have their own 'this', they return the value of this where they are written
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
