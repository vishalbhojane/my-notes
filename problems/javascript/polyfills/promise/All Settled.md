Promises

```js
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve('p1 resolved')
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
Promise.allSettled([p1, p2]).then(res => console.log(res)).catch(err => console.log(err))

```

Solution

```js
Promise.myallSettled = function (promiseArray) {
    let counter = 0;
    const result = [];

    return new Promise((resolve, reject) => {
        promiseArray.forEach((promise, i) => {
            promise.then((res) => {
                result[i] = { status: 'fulfilled', value: res }
            }).catch(err => {
                result[i] = { status: 'rejected', reason: err }
            }).finally(() => {
                counter++
                if (counter === promiseArray.length) {
                    resolve(result)
                }
            })
        })
    })
}

Promise.myallSettled([p1,p2]).then(res => console.log(res)).catch(err => console.log(err))
```

**Steps**
initialise counter `0` and result `[]`
return a promise
loop over promiseArray, store responce in result`[]` `{status, value}`
if any promise fails, store `{status, reaseon}`
finally `resolve` with result`[]`