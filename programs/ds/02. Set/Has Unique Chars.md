Create a function `hasUniqueChars` that determines whether a given string contains only unique characters. The function should:
1. Accept a string as input.
2. Return true if all characters in the string are unique.
3. Return false if there are any duplicate characters.
4. Handle empty strings and strings of any length.

## Solution

```javascript
function hasUniqueChars(string) {
    const charSet = new Set();

    for (const ch of string) {
        if (charSet.has(ch)) {
            return false;
        }
        charSet.add(ch);
    }

    return true;
}
```

Core Logic:
1. Use a Set to keep track of characters seen.
2. Iterate through each character in the string.
3. If a character is already in the Set, return false (not unique).
4. If we finish iterating without finding duplicates, return true.

## Solution 2 

```javascript
function hasUniqueChars(string) {
    return new Set(string).size === string.length;
}
```

Core Logic:
1. Create a Set from the string, which automatically removes duplicates.
2. Compare the size of the Set to the length of the original string.
3. If they're equal, all characters were unique; if not, there were duplicates.

Usage

```javascript
console.log(hasUniqueChars("abcdefg")); // true
console.log(hasUniqueChars("hello")); // false
console.log(hasUniqueChars("")); // true
console.log(hasUniqueChars("0123456789")); // true
console.log(hasUniqueChars("abcABC")); // true
```