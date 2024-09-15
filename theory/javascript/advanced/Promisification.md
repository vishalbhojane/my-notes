Promisification is the process of converting a call-back-based function into a [[notes/theory/javascript/advanced/Promise|Promise]]-based one

Call-back

```js
function loadScript(src, callback) {
    const script = document.createElement('script')

    script.src = src

    script.onload = function () {
        return callback(null, script) // usually callbacks have first argument for error and second for success
    }

    script.onerror = function (err) {
        return callback(err)
    }

    document.head.append(script)
}

loadScript('test.js', function (err, script) {
    if (err) {
        console.log(err)
    } else {
        console.log(script)
    }
})
```

Promisify Function

```js
function promisify(fun) {
    return function (...args) { // return a wrapper-function 
        return new Promise((resolve, reject) => {
            function callback(err, result) { // our custom callback for f 
                if (err) {
                    reject(err);
                } else {
                    resolve(result);
                }
            }

            args.push(callback); // append our custom callback to the end of f arguments

            fun.call(this, ...args); // call the original function
        });
    };
}
```

Usage

Simple function

```js
const loadScriptPromisified = promisify(loadScript)

loadScriptPromisified('test.js')
    .then(function () {
        console.log('done')
    }).catch(function (err) {
        console.log(err)
    })
```

Class method

```js
class Example {
    constructor(a) {
        this.a = a;
    }
    method(b, callback) {
        const result = this.a + b;
        setTimeout(() => callback(null, result), 100);
    }
}

(async () => {
    try {
        const e = new Example(40);
        const promisifiedMethod = promisify(e.method);
        const result = await promisifiedMethod.call(e, 2);
        console.log(result);
    } catch (error) {
        console.error(error);
    }
})();
```
