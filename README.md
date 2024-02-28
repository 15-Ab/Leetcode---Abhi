# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 28-02-24 [Problem Link](https://leetcode.com/problems/find-bottom-left-tree-value/description/?envType=daily-question&envId=2024-02-28)
## 513. Find Bottom Left Tree Value

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
To find the leftmost value in the bottom row of a binary tree, I can perform a level order traversal (BFS) of the tree. During the traversal, I keep updating a variable to store the leftmost node at each level. Once the traversal is complete, the variable will contain the leftmost node in the bottom row.

# Approach
<!-- Describe your approach to solving the problem. -->
- I initialized a variable (`leftMost`) to store the leftmost node.
- Used a queue to perform level order traversal.
- Enqueued the root of the tree.
- While the queue is not empty :
   - Dequeued a node and update `leftMost` with its value.
   - Enqueued the right child if it exists.
   - Enqueued the left child if it exists.
- After the traversal, `leftMost` will contain the leftmost node in the bottom row.
- Returned the value of the leftmost node.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)

# Complexity
- Time complexity : $O(N)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$N$ : number of nodes in the binary tree

- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

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
    
    // Static variable to store the leftmost node
    static TreeNode leftMost;
    
    // Queue to perform level order traversal
    static Queue<TreeNode> q;
    
    // Method to find the leftmost value in the bottom row of the binary tree
    public int findBottomLeftValue(TreeNode root) {
        
        // Initializing the leftMost and queue
        leftMost = null;
        q = new LinkedList<>();
        q.offer(root);

        // Performing level order traversal
        while (!q.isEmpty()) {
            // Retrieving the front node of the queue and update leftMost
            leftMost = q.poll();
            
            // Enqueueing the right child if it exists
            if (leftMost.right != null) {
                q.offer(leftMost.right);
            }
            
            // Enqueueing the left child if it exists
            if (leftMost.left != null) {
                q.offer(leftMost.left);
            }
        }
        
        // Returning the value of the leftmost node in the bottom row
        return leftMost.val;
    }
}
```