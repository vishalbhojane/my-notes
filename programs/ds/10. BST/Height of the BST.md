Create a function `height` that calculates the height of a binary tree. The function should:

1. Handle any valid binary tree, including empty trees.
2. Return the height of the tree, where height is defined as the number of edges in the longest path from the root to a leaf.
3. Use an efficient recursive algorithm to solve the problem.

```javascript
class Solution {
    height(node) {
        if (node === null) {
            return -1;
        }
        
        let leftHeight = this.height(node.left);
        let rightHeight = this.height(node.right);
        
        return Math.max(leftHeight, rightHeight) + 1;
    }
}
```

Core Logic:
1. Use recursion to traverse the tree.
2. For each node, calculate the height of its left and right subtrees.
3. The height of a node is the maximum of its subtrees' heights plus one.
4. An empty tree (null node) has a height of -1.

Time Complexity: O(n), where n is the number of nodes in the tree. Each node is visited once.

Space Complexity: O(h), where h is the height of the tree. This space is used by the recursive call stack.

Usage

```javascript
// Assuming we have a Node class and a way to construct a tree
let tree = new Node(12);
tree.left = new Node(8);
tree.right = new Node(18);
tree.left.left = new Node(5);
tree.left.right = new Node(11);

let solution = new Solution();
console.log(solution.height(tree)); // Output: 2

// More test cases
console.log(solution.height(null)); // Output: -1
console.log(solution.height(new Node(1))); // Output: 0

let singleChildTree = new Node(1);
singleChildTree.left = new Node(2);
console.log(solution.height(singleChildTree)); // Output: 1
```
