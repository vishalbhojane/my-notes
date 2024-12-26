The `**findLongestString**` function aims to find the longest string from an array of strings (`**stringArray**`).  
  
The function returns the longest string present in the given array.

  

**Constraints:**

- The array can be empty or contain any number of elements.
    
- Elements in the array must be strings.
    
- If there are multiple strings of the same longest length, the function returns the first one it encounters.
    

  

**Parameters:**

- `**stringArray**`: An array of strings.
    

  

**Returns:**

- The function returns the longest string from the array `**stringArray**`.
    
- If `**stringArray**` is empty, the function returns an empty string `**""**`.
    

  

**Examples:**

1. **Basic Example**
    
    1. let myStrings = ["apple", "banana", "pea"];
    2. let result = findLongestString(myStrings);
    3. // The function should return "banana"
    
2. **Array with Single Character Strings**
    
    1. let myStrings = ["a", "b", "c"];
    2. let result = findLongestString(myStrings);
    3. // The function should return "a"
    
3. **Array with Multiple Longest Strings**
    
    1. let myStrings = ["orange", "cherry", "banana"];
    2. let result = findLongestString(myStrings);
    3. // The function should return "orange"
    
4. **Array with Empty Strings**
    
    1. let myStrings = ["", "", ""];
    2. let result = findLongestString(myStrings);
    3. // The function should return ""
    
5. **Array with Mixed Length Strings**
    
    1. let myStrings = ["apple", "a", "banana", "bb"];
    2. let result = findLongestString(myStrings);
    3. // The function should return "banana"
    
6. **Empty Array**
    
    1. let myStrings = [];
    2. let result = findLongestString(myStrings);
    3. // The function should return ""
    

  

Note: The function assumes that the array contains strings. If you expect to encounter non-string elements, you should handle that separately before calling `**findLongestString**`.


```js
function findLongestString(stringArray) {
    let longestString = "";
    for (let str of stringArray) {
        if (str.length > longestString.length) {
            longestString = str;
        }
    }
    return longestString;
}
```

