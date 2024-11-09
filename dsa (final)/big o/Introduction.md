Big O is to describe the time complexity or space complexity of algorithms.

Time complexity is a measure of how long an algorithm takes to run as the input size increases.
Space complexity is a way to measure how much memory an algorithm needs to run.

---

There are three ways to define the time complexity
- Omega (Ω)
- Theta (Θ)
- Omicron / Big O (O)

Consider We are finding an element in an array `[1,2,3,4,5,6,7]`
- If we are looking for the number `1`  , then this is our best case (Ω)
- number `4` is an average case
- and lastly, number `7` would be worst case (O), since we had to traverse entire array

---
### O(n) - Linear Time

```js
function logItems(n) {
    for (let i = 0; i < n; i++) {
        console.log(i);
    }
}

logItems(10);
```

Above code rans for `n` times, hence it is an O(n) operation

---
### O(n^2)

```js
function logItems(n) {
    for (let i = 0; i < n; i++) {
        for (let j = 0; j < n; j++) {
            console.log(i, j);
        }
    }
}

logItems(10);
```

Above code rans for `n * n` times, i.e. *n^2* times, hence it is an O(n^2) operation.

---
### O(1) - Constant Time

```js
function addItems(n){
    return n + n;
}

addItems(1);
```

In above code there is only one operation (there is one + operator), i.e. it will run only once, independent of input size, hence it is O(1)

```js
function addItems(n){
    return n + n + n
}

addItems(1);
```

Above code has two operations (there are two + operators), i.e. it will run 2 times, hence we can say that it is a O(2) operations. to simplify further we can say it is a O(1)

---
### O(log n)

Consider a sorted array `[1,2,3,4,5,6,7,8]`, and we are looking for a number `1`

Here is our algorithm
We split the array into half
Check if the number is in first half or second half
If not in second half or first, we don't even go through that half
If we find the item we return the number
	else Repeat from step 1

For above input size, i.e. 8, we did 3 operations to get the number `1`, 
2^3 = 8
log (base 2) 3 = 8

This is useful for larger input size, consider a number 1073741824
2^? = this number, answer is 31
log (base 2) 31 = 1073741824
So we only did 31 operations, which is far better than linear times, i.e. going through each items at-least once

---
##### Drop constants

```js
function logItems(n){
    for(let i = 0; i < n; i++){
        console.log(i);
    }
    for(let j = 0; j < n; j++){
        console.log(j);
    }
}

logItems(10);
```

Above code runs for *n + n* times, i.e. *2n* times, and time complexity would be O(2n).
To simplify we drop the constants. hence code becomes O(n).

##### Drop non dominants

```js
function logItems(n) {
    for (let i = 0; i < n; i++) {
        for (let j = 0; j < n; j++) {
            console.log(i, j);
        }
    }

    for (let k = 0; k < n; k++) {
        console.log(k);
    }
}

logItems(10);
```

In above code first loops runs for `n^2` times and second runs for `n` times, hence total would be `n^2 + n`
But if think in terms of input size, consider 100. n^2 would be 10000,  so 10000 + 100. here 100 is not really affecting the number of operations. Hence n^2 is a dominant term and n is a non-dominant, and we drop non dominants.

##### Different terms for input

```js
function logItems(a, b) {
    for (let i = 0; i < a; i++) {
        console.log(i);
    }
    for (let j = 0; j < b; j++) {
        console.log(j);
    }
}

logItems(10, 5);
```

Here `a` and `b` are independent, and may or may not be equal. so the time complexity here is 
O(a + b)

```js
function logItems(a, b) {
    for (let i = 0; i < a; i++) {
        for (let j = 0; j < b; j++) {
            console.log(i, j);
        }
    }
}

logItems(10, 5);
```

For above nested loop, it is O(a * b)

---

### Big O for Array

```js
const arr = [1,2,4,5,6,7]

arr.push(8)     // O(1)
arr.pop()       // O(1)
arr.unshift(9)  // O(n)
arr.shift()     // O(n)

arr.splice(     // O(n)
    0,      // starting Pos
    1,      // number of items to remove
    2, 3    // items to add
)
```


---
##### Example

For n = 100
O(1) = 1
O(log n) ~ 7
O(n) = 100
O(n^2) = 10000

For n = 1000
O(1) = 1
O(log n) ~ 10
O(n) = 1000
O(n^2) = 1000000 

---

O(1) = Constant 
O(log n) = Divide and Conquer
O(n) = Proportional
O(n^2) = Loop with in loop

---

[Useful resource to see Big O](https://www.bigocheatsheet.com/)

---
### Quiz

##### What is the Big O time complexity when you have a loop within a loop?
O(n^2)

##### How would the following be written:  O(100n^2)
O(n^2)
We drop constants.

##### What Big O is associated with Divide and Conquer?
O(log n)

##### What is the correct way to write:  O(n^2 + n)
O(n^2)
We drop non-dominants.

##### The most efficient Big O is:
O(1)
O(1) is also known as constant time.