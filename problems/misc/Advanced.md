## What is the difference between these four promises?

```js
doSomething().then(function () {
  return doSomethingElse();
});

doSomething().then(function () {
  doSomethingElse();
});

doSomething().then(doSomethingElse());

doSomething().then(doSomethingElse);
```

These four promise chains differ in how they handle the return values and the execution flow. Let’s break down each one:

#### 1. **`doSomething().then(function () { return doSomethingElse(); });`**

- **Explanation**: Inside the `then()` block, `doSomethingElse()` is **called** and **returned**.
- **Effect**:
    - The promise chain will wait for the `doSomethingElse()` promise to **resolve** before continuing.
    - The return value of `doSomethingElse()` (which is likely a promise) will become the result of this `then()` block.

#### 2. **`doSomething().then(function () { doSomethingElse(); });`**

- **Explanation**: Inside the `then()` block, `doSomethingElse()` is **called**, but the function doesn’t return it.
- **Effect**:
    - `doSomethingElse()` is called, but its result is **not awaited**.
    - The promise chain will proceed without waiting for `doSomethingElse()` to resolve, since nothing is returned.
    - The next `then()` block (if there is one) will execute immediately after `doSomething()` resolves, regardless of `doSomethingElse()`'s state.

#### 3. **`doSomething().then(doSomethingElse());`**

- **Explanation**: `doSomethingElse()` is **immediately executed** when the code runs, and its result is passed to the `then()` method.
- **Effect**:
    - `doSomethingElse()` is called **immediately** (before `doSomething()` even finishes).
    - The result of `doSomethingElse()` is passed as an argument to `then()`, but this is not the expected behavior for a promise chain.
    - This will likely cause unexpected behavior because `doSomethingElse()` is executed too early.

#### 4. **`doSomething().then(doSomethingElse);`**

- **Explanation**: `doSomethingElse` is passed as a **callback** to `then()`, but it is not executed immediately.
- **Effect**:
    - `doSomethingElse` will be called **after** `doSomething()` resolves.
    - The promise chain will correctly wait for `doSomething()` to resolve, and then execute `doSomethingElse()`.
    - If `doSomethingElse` returns a promise, the chain will wait for it to resolve.

#### Summary:

- **1st**: Properly returns and waits for `doSomethingElse()`.
- **2nd**: Calls `doSomethingElse()` but doesn't wait for it.
- **3rd**: Calls `doSomethingElse()` **immediately**, which is incorrect in most cases.
- **4th**: Passes `doSomethingElse` as a callback, executed only when `doSomething()` resolves.