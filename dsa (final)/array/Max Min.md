The `**findMaxMin**` function takes an array of numbers (`**myArray**`) as its input.  
  
The function aims to find both the maximum and minimum values present in the array.  
  
It returns an array containing two elements: the first being the maximum value and the second being the minimum value found in `**myArray**`.

  
**Constraints:**

- The array must contain at least one element.
    
- The array can contain integers or floating-point numbers.
    
- Do not use built-in `**Math.max**` or `**Math.min**` functions.
    
- You are not allowed to sort the array.
    

  
**Parameters:**

- `**myArray**`: An array of numbers, either integers or floats.
    

  
**Returns:**

- The function returns an array `**[maximum, minimum]**`, where `**maximum**` is the largest number and `**minimum**` is the smallest number in `**myArray**`.
    

  

**Examples:**

1. **Basic Example**
    
    1. let myArray = [3, 2, 4, 1];
    2. let result = findMaxMin(myArray);
    3. // The function should return [4, 1]
    
2. **Array with Negative Numbers**
    
    1. let myArray = [-1, -2, -3, -4];
    2. let result = findMaxMin(myArray);
    3. // The function should return [-1, -4]
    
3. **Array with Same Numbers**
    
    1. let myArray = [5, 5, 5, 5];
    2. let result = findMaxMin(myArray);
    3. // The function should return [5, 5]
    
4. **Array with One Element**
    
    1. let myArray = [7];
    2. let result = findMaxMin(myArray);
    3. // The function should return [7, 7]
    
5. **Array with Floating-Point Numbers**
    
    1. let myArray = [1.1, 2.2, 0.9, 3.7];
    2. let result = findMaxMin(myArray);
    3. // The function should return [3.7, 0.9]
    
6. **Array with Mixed Positive and Negative Numbers**
    
    1. let myArray = [-1, 2, -3, 4];
    2. let result = findMaxMin(myArray);
    3. // The function should return [4, -3]
    

  

Note: The function assumes that the array is not empty. If you expect to encounter empty arrays, you should handle that separately before calling `**findMaxMin**`.

```js
function findMaxMin(myArray) {
    let maximum = myArray[0];
    let minimum = myArray[0];
    for (let num of myArray) {
        if (num > maximum) {
            maximum = num;
        } else if (num < minimum) {
            minimum = num;
        }
    }
    return [maximum, minimum];
}
```

