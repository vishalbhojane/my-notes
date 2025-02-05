Create a function `diameter` that calculates the diameter of a binary tree. The function should:

1. Handle any valid binary tree, including empty trees.
2. Return the diameter of the tree, where diameter is defined as the number of edges on the longest path between any two leaf nodes.
3. Use an efficient recursive algorithm to solve the problem.

```javascript
class Solution {
    constructor() {
        this.maxDiameter = 0;
    }

    diameter(root) {
        this.maxDiameter = 0;
        this.dfs(root);
        return this.maxDiameter;
    }

    dfs(node) {
        if (node === null) {
            return 0;
        }
        
        let leftHeight = this.dfs(node.left);
        let rightHeight = this.dfs(node.right);
        
        this.maxDiameter = Math.max(this.maxDiameter, leftHeight + rightHeight);
        
        return Math.max(leftHeight, rightHeight) + 1;
    }
}
```

Core Logic:
1. Use a depth-first search (DFS) approach to traverse the tree.
2. For each node, calculate the height of its left and right subtrees.
3. Update the maximum diameter by comparing it with the sum of left and right subtree heights.
4. Return the height of the current subtree (max of left and right heights plus one).
5. The final diameter is stored in the `maxDiameter` variable.

Time Complexity: O(n), where n is the number of nodes in the tree. Each node is visited once.

Space Complexity: O(h), where h is the height of the tree. This space is used by the recursive call stack.

Usage

```javascript
// Assuming we have a Node class and a way to construct a tree
let tree = new Node(1);
tree.left = new Node(2);
tree.right = new Node(3);
tree.left.left = new Node(4);
tree.left.right = new Node(5);

let solution = new Solution();
console.log(solution.diameter(tree)); // Output: 3

// More test cases
console.log(solution.diameter(null)); // Output: 0
console.log(solution.diameter(new Node(1))); // Output: 0

let linearTree = new Node(1);
linearTree.right = new Node(2);
linearTree.right.right = new Node(3);
console.log(solution.diameter(linearTree)); // Output: 2
```