Create a function `reverseString(string)` that reverses a given string using a stack. The function should:
1. Use a Stack data structure to reverse the order of characters.
2. Handle strings of any length, including empty strings.
3. Return the reversed string.

## Solution

```javascript
function reverseString(string) {
    const stack = new Stack();
    let reversedString = "";

    // Push all characters onto the stack
    for (const c of string) {
        stack.push(c);
    }

    // Pop characters from the stack to form the reversed string
    while (!stack.isEmpty()) {
        reversedString += stack.pop();
    }

    return reversedString;
}
```

Core Logic:
1. Create a new Stack instance to store characters.
2. Iterate through each character in the input string, pushing it onto the stack.
3. Pop characters from the stack and append them to a new string.
4. The resulting string will be the reverse of the input string.

Usage

```javascript
console.log(reverseString("hello"));  // "olleh"
console.log(reverseString("OpenAI")); // "IAnepO"
console.log(reverseString(""));       // ""
console.log(reverseString("a"));      // "a"
```

## Complexity

Time = O(n), where n is the length of the input string, as it iterates through the string twice (once to push onto the stack, once to pop from the stack)
Space = O(n) as it stores all characters in the stack.