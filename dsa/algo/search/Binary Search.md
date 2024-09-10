```
works on sorted array
compare target with middle element
if target is small, check in left half of array else in right
```

```js
function binarySearch(arr, t){
    let leftIndex = 0
    let rightIndex = arr.length - 1

    while(leftIndex <= rightIndex){
        let middleIndex = Math.floor((leftIndex + rightIndex) / 2)
        let el = arr[middleIndex]
        if(el === t){
            return middleIndex
        }
        if(t < el){
            rightIndex = middleIndex - 1
        } else {
            leftIndex = middleIndex + 1
        }
    }
    return -1
}

console.log(binarySearch([1, 2, 3, 4], 3))
console.log(binarySearch([1, 2, 3, 4], 1))
```

Time Complexity
O(log n)

## Using Recursion

```js
function binarySearch(arr, t){
    return search(arr, t, 0, arr.length - 1)
}

function search(arr, t, leftIndex, rightIndex){
    if(leftIndex > rightIndex){
        return -1
    }

    let middleIndex = Math.floor((leftIndex + rightIndex) / 2)

    if(arr[middleIndex] === t){
        return middleIndex
    }

    if(t < arr[middleIndex]){
        return search(arr, t, leftIndex, middleIndex - 1)
    } else {
        return search(arr, t, middleIndex + 1, rightIndex)
    }
}

console.log(binarySearch([1, 2, 3, 4], 3))
console.log(binarySearch([1, 2, 3, 4], 5))
```

