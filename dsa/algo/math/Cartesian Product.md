In mathematics, the Cartesian Product of sets A and B is defined as the set of all ordered pairs (x, y) such that x belongs to A and y belongs to B. For example, if A = {1, 2} and B = {3, 4, 5}, then the Cartesian Product of A and B is {(1, 3), (1, 4), (1, 5), (2, 3), (2, 4), (2, 5)}

```js
function cartesianProduct(arr1, arr2){
    const result = [];

    for(let i = 0; i < arr1.length; i++){
        for(let j = 0; j < arr2.length; j++){
            result.push([arr1[i], arr2[j]])
        }
    }

    return result
}

console.log(cartesianProduct([1,2], [3,4,5]))
```

Time Complexity
O (n * m)
*Time complexity depends on length of arr1 and arr2*
