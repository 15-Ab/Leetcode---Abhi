# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 08-01-24 [Problem Link](https://leetcode.com/problems/range-sum-of-bst/description/)
## 938. Range Sum of BST

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

My code will perform an inorder traversal to selectively accumulate values within the specified range.

---
# Approach
<!-- Describe your approach to solving the problem. -->
- Inorder Traversal :
- - I implemented a recursive inorder traversal function that follows the BST properties :
- - - Recursively traversed the left subtree.
- - - Checked if the current node's value is within the specified range [low, high].
- - - If true, thrn added the value to the sum.
- - - Recursively traversed the right subtree.
- Main Method (rangeSumBST) :
- - Initialized the static variables (jor, l, h) to store the sum and the low and high values.
- - Initialized 'jor' to zero.
- - Set the low and high values based on the input parameters.
- - Called the inorder method starting from the root of the BST.
- - Returned the final sum.
---
# Optimizations
- The use of static variables allows for state retention, avoiding the need for passing parameters across recursive calls.
- The 'inorder' traversal efficiently considers only nodes that could contribute to the sum within the specified range, enhancing performance.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

---
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $O(h)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
---
$n$ : number of nodes
$h$ : height of tree

---
# Code
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    // Static variables to store the sum, low, and high values
    static int jor;
    static int l;
    static int h;

    // Main method to calculate the range sum in the BST
    public int rangeSumBST(TreeNode root, int low, int high) {
        // Initialize the sum, low, and high values
        jor = 0;
        l = low;
        h = high;

        // Perform inorder traversal to calculate the sum within the specified range
        inorder(root);

        // Return the final sum
        return jor;
    }

    // Helper method for inorder traversal
    static void inorder(TreeNode r) {
        // Base case: if the current node is null, return
        if (r == null) {
            return;
        }

        // Recursively traverse the left subtree
        inorder(r.left);

        // Check if the value of the current node is within the specified range [low, high]
        if (r.val >= l && r.val <= h) {
            // If yes, add the value to the sum
            jor += r.val;
        }

        // Recursively traverse the right subtree
        inorder(r.right);
    }
}

```
