```js
function quick(arr) {

    if (arr.length < 2) {
        return arr
    }

    let pivot = arr[arr.length - 1]
    let left = []
    let right = []

    for (let i = 0; i < arr.length - 1; i++) {
        if (arr[i] < pivot) {
            left.push(arr[i])
        } else {
            right.push(arr[i])
        }
    }

    return [...quick(left), pivot, ...quick(right)]
}

console.log(quick([3,2,1,5,4]))
```

Time Complexity
Average
O(n log n)

Worst - if the array is already sorted
O(n^2) 

