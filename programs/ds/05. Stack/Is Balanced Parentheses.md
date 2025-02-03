Create a function `isBalancedParentheses(parentheses)` that checks if a string of parentheses is balanced. The function should:
1. Use a Stack data structure to keep track of opening parentheses.
2. Handle strings of any length, including empty strings.
3. Return true if the parentheses are balanced, false otherwise.

## Solution

```javascript
function isBalancedParentheses(parentheses) {
    const stack = new Stack();

    for (const p of parentheses) {
        if (p === '(') {
            stack.push(p);
        } else if (p === ')') {
            if (stack.isEmpty() || stack.pop() !== '(') {
                return false;
            }
        }
    }

    return stack.isEmpty();
}
```

Core Logic:
1. Create a new Stack instance to store opening parentheses.
2. Iterate through each character in the input string:
   - If it's an opening parenthesis '(', push it onto the stack.
   - If it's a closing parenthesis ')', check if the stack is empty or the top of the stack isn't an opening parenthesis. If either condition is true, return false.
3. After processing all characters, return true if the stack is empty (all parentheses matched), false otherwise.

Usage

```javascript
console.log(isBalancedParentheses("(())"));   // true
console.log(isBalancedParentheses("()()"));   // true
console.log(isBalancedParentheses("(()())"));  // true
console.log(isBalancedParentheses("(()")); // false
console.log(isBalancedParentheses(")("));  // false
console.log(isBalancedParentheses(""));    // true
```

## Complexity

Time = O(n), where n is the length of the input string, as it iterates through the string once.
Space = O(n) in the worst case, where all characters are opening parentheses.
