```
assume 1st element is sorted
comare next element with the sorted elements
```

```js
function insertion(arr){
    for(let i = 1; i < arr.length; i++){
        let current = arr[i]
        let j = i - 1;
        while((j >= 0) && (arr[j] > current)){
            arr[j + 1] = arr[j]
            j-- 
        }
        arr[j + 1] = current
    }
    return arr
}

console.log(insertion([3,2,1,5,4]))
```

Time Complexity
O(n^2)