Create a function `mirror` that converts a binary tree to its mirror image. The function should:

1. Handle any valid binary tree, including empty trees.
2. Swap the left and right children of every node.
3. Use an efficient recursive algorithm to solve the problem.

```javascript
class Solution {
    mirror(node) {
        // Base case: if the node is null, return null
        if (node === null) {
            return null;
        }
        
        // Swap the left and right children
        let temp = node.left;
        node.left = node.right;
        node.right = temp;
        
        // Recursively mirror the left and right subtrees
        this.mirror(node.left);
        this.mirror(node.right);
        
        // Return the mirrored node
        return node;
    }
}
```

Core Logic:
1. Use recursion to traverse the tree.
2. For each non-null node, swap its left and right children.
3. Recursively apply the same process to the left and right subtrees.
4. An empty tree (null node) remains unchanged.

Time Complexity: O(n), where n is the number of nodes in the tree. Each node is visited once.

Space Complexity: O(h), where h is the height of the tree. This space is used by the recursive call stack.

Usage:

```javascript
// Assuming we have a Node class and a way to construct a tree
let tree = new Node(1);
tree.left = new Node(2);
tree.right = new Node(3);
tree.left.left = new Node(4);
tree.left.right = new Node(5);

let solution = new Solution();
let mirroredTree = solution.mirror(tree);

// Function to print tree in-order (for verification)
function inOrder(node) {
    if (node === null) return;
    inOrder(node.left);
    console.log(node.data);
    inOrder(node.right);
}

console.log("Original tree:");
inOrder(tree);
console.log("Mirrored tree:");
inOrder(mirroredTree);

// More test cases
console.log(solution.mirror(null)); // Output: null

let singleNodeTree = new Node(1);
console.log(solution.mirror(singleNodeTree).data); // Output: 1

let unbalancedTree = new Node(1);
unbalancedTree.left = new Node(2);
unbalancedTree.left.left = new Node(3);
let mirroredUnbalanced = solution.mirror(unbalancedTree);
console.log(mirroredUnbalanced.right.right.data); // Output: 3
```

