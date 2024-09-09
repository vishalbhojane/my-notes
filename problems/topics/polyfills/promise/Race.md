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
Promise.race([p1,p2]).then(res => console.log(res)).catch(err => console.log(err))
```

Solution

```js
Promise.myrace = function(promiseArray) {
    return new Promise((resolve, reject) => {
        promiseArray.forEach((promise, i) => {
            promise.then((res) => {
                resolve(res)
            }).catch(err => {
                reject(err)
            })
        })
    })
}

Promise.myrace([p1,p2]).then(res => console.log(res)).catch(err => console.log(err))
```

**Steps**
initialise counter `0` and result `[]`
return a promise
loop over promiseArray, store responce in result`[]`
`reject` if any promise fails