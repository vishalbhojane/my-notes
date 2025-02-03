Create a function `firstNonRepeatingChar(string)` that finds the first non-repeating character in a given string. The function should:
1. Use a Map to count occurrences of each character in the string.
2. Return the first character that appears only once, or null if no such character exists.
3. Handle strings of any length, including empty strings.

## Solution

```javascript
function firstNonRepeatingChar(string) {
    const charCounts = new Map();

    // Count occurrences of each character
    for (let i = 0; i < string.length; i++) {
        const c = string.charAt(i);
        charCounts.set(c, (charCounts.get(c) || 0) + 1);
    }

    // Find the first character with count 1
    for (let i = 0; i < string.length; i++) {
        const c = string.charAt(i);
        if (charCounts.get(c) === 1) {
            return c;
        }
    }

    // No non-repeating character found
    return null;
}
```

Core Logic:
1. Create a Map to store the count of each character in the input string.
2. Iterate through the string once to count character occurrences.
3. Iterate through the string again to find the first character with a count of 1.
4. Return the first non-repeating character or null if none exists.

Usage

```javascript
console.log(firstNonRepeatingChar("programming")); // "p"
console.log(firstNonRepeatingChar("aabbcdeeff"));  // "c"
console.log(firstNonRepeatingChar("aabbcc"));      // null
console.log(firstNonRepeatingChar(""));            // null
console.log(firstNonRepeatingChar("stress"));      // "t"
```
