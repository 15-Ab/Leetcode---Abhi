# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 11-01-24 [Problem Link](https://leetcode.com/problems/maximum-difference-between-node-and-ancestor/description/)
## 1026. Maximum Difference Between Node and Ancestor


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My code aims to find the maximum absolute difference between the values of any two nodes in the same path from the root to a leaf in a binary tree. It utilizes a recursive approach to traverse the tree while maintaining the minimum and maximum values encountered along the path.

# Approach
<!-- Describe your approach to solving the problem. -->
**Base Case:**
   - If the root is null, returned 0 as there are no nodes to compare.

**Recursive Calculation:**
   - My `maxAncestorDiff` method takes three parameters: the current node `r`, the minimum value encountered so far `chota`, and the maximum value encountered so far `bara`.
   - Updated `chota` and `bara` based on the current node's value.
   - Calculated the current absolute difference (`currentDifference`) between `bara` and `chota`.

**Recursive Calls for Left and Right Subtrees:**
   - Recursively called `maxAncestorDiff` on the left subtree if it exists and updated `leftChildMax` with the result.
   - Recursively called `maxAncestorDiff` on the right subtree if it exists and updated `rightChildMax` with the result.

**Calculate Maximum Difference:**
   - Calculated the maximum difference from the left and right subtrees (`maxFromChild`).
   - Returned the maximum value among the current path and the subtrees.

**Result:**
   - The result is the maximum absolute difference among the values of any two nodes in the same path from the root to a leaf.
---
Have a look at the code , still have any confusion then please let me know in the comments Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of nodes
- Space complexity : $O(h)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$h$ : height of tree
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
    
    public int maxAncestorDiff(TreeNode root) {
        // Checked if the tree is empty
        if (root == null) {
            return 0;
        }
        // Called the helper method with the root and initial min/max values
        return maxAncestorDiff(root, root.val, root.val);
    }

    // Helper method to calculate the maximum ancestor difference recursively
    static int maxAncestorDiff(TreeNode r, int chota, int bara) {
        // Update the min and max values for the current path
        chota = Math.min(chota, r.val);
        bara = Math.max(bara, r.val);

        // Calculated the current difference between min and max values in the path
        int currentDifference = bara - chota;

        // Initialized variables for maximum differences from left and right subtrees
        int leftChildMax = 0;
        int rightChildMax = 0;

        // Recursively calculated the maximum difference from the left subtree
        if (r.left != null) {
            leftChildMax = maxAncestorDiff(r.left, chota, bara);
        }

        // Recursively calculated the maximum difference from the right subtree
        if (r.right != null) {
            rightChildMax = maxAncestorDiff(r.right, chota, bara);
        }

        // Calculated the maximum difference among the current path and subtrees
        int maxFromChild = Math.max(leftChildMax, rightChildMax);

        // Returned the maximum difference among the current path and subtrees
        return Math.max(maxFromChild, currentDifference);
    }
}

```
