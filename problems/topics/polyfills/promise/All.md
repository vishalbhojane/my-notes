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
Promise.all([p1,p2]).then(res => console.log(res)).catch(err => console.log(err))
```

Solution

```js
Promise.myall = function(promiseArray) {
    let counter = 0;
    const result = [];

    return new Promise((resolve, reject) => {
        promiseArray.forEach((promise, i) => {
            promise.then((res) => {
                result[i] = res
                counter++

                if(counter === promiseArray.length){
                    resolve(result)
                }
            }).catch(err => {
                reject(err)
            })
        })
    })
}

Promise.myall([p1,p2]).then(res => console.log(res)).catch(err => console.log(err))
```

**Steps**
initialise counter `0` and result `[]`
return a promise
loop over `promiseArray`, store response in result `[]`
`reject` if any promise fails