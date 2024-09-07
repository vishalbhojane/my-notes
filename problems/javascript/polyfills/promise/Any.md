Promises

```js
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        // resolve('p1 resolved')
        reject('p1 resolved')

    }, 2000)
})

const p2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        // resolve('p2 resolved')
        reject('p2 rejected')
    }, 1000)
})
```

Usage

```js
Promise.any([p1, p2]).then(res => console.log(res)).catch(err => console.log(err))
```

Solution

```js
Promise.myany = function (promiseArray) {
    const result = [];
    let counter = 0;

    return new Promise((resolve, reject) => {
        promiseArray.forEach((promise, i) => {
            promise.then((res) => {
                resolve(res)
            }).catch(err => {
                result[i] = err
                counter++
                if (counter === promiseArray.length) {
                    const aggError = new AggregateError(result, 'All promises were rejected')
                    reject(aggError)
                }
            })
        })
    })
}

Promise.myany([p1, p2]).then(res => console.log(res)).catch(err => console.log(err))
```

**Steps**
initialise counter `0` and result `[]`
return a promise
loop over promiseArray, store responce in result`[]` `{status, value}`
if any promise fails, store `{status, reaseon}`
finally `resolve` with result`[]`