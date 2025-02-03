You are given a string s consisting of lowercase English letters. Your task is to perform the following operation exactly once:

1. Select any non-empty substring of s.
2. Replace every letter in the selected substring with the letter that comes before it in the alphabet. (For example, 'b' becomes 'a', and 'a' becomes 'z')

Your goal is to return the lexicographically smallest string possible after performing this operation.

Constraints:
- The length of s is between 1 and 3 * 10^5.
- s contains only lowercase English letters.

Examples:
1. Input: s = "cbabc"
   Output: "baabc"

2. Input: s = "acbbc"
   Output: "abaab"

3. Input: s = "leetcode"
   Output: "kddsbncd"

4. Input: s = "aa"
   Output: "az"

Note: A string a is lexicographically smaller than a string b if in the first position where a and b differ, string a has a letter that appears earlier in the alphabet than the corresponding letter in b.

Your task is to implement a function that takes the string s as input and returns the lexicographically smallest string possible after performing the described operation.

```javascript
var smallestString = function(s) {
    let index = 0;
    const n = s.length;
    
    // Skip leading 'a's
    while (index < n && s[index] === 'a') {
        index++;
    }
    
    // If all characters are 'a', change the last one to 'z'
    if (index === n) {
        return s.slice(0, -1) + 'z';
    }
    
    // Convert to array for easier manipulation
    let chars = s.split('');
    
    // Convert each non-'a' character to its preceding letter
    while (index < n && chars[index] !== 'a') {
        chars[index] = String.fromCharCode(chars[index].charCodeAt(0) - 1);
        index++;
    }
    
    // Join back into a string and return
    return chars.join('');
};
```

This solution has a time complexity of O(n) where n is the length of the string, as we potentially need to traverse the entire string once. The space complexity is also O(n) due to the conversion of the string to an array of characters.