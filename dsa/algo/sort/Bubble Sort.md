
```
compare adjucent elements
if left element is bigger, swap
repeat until there is no swap
```

```js
function bubble(arr) {
    let isSwapped = true

    while (isSwapped) {
        isSwapped = false
        for (let i = 0; i < arr.length - 1; i++) {
            if (arr[i] > arr[i + 1]) {
                let temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
                isSwapped = true
            }
        }
    }z

    return arr
}

console.log(bubble([3,2,1,5,4]))
```

Time Complexity
O(n^2)