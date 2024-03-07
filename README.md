# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 07-03-24 [Problem Link](https://leetcode.com/problems/middle-of-the-linked-list/description/?envType=daily-question&envId=2024-03-07)
## 876. Middle of the Linked List

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We are given a singly-linked list and need to find its middle node.

# Approach
<!-- Describe your approach to solving the problem. -->
To find the middle node, I followed these steps : 
- I calculated the length of the linked list using a helper function.
- Traversed the linked list to find the middle node.
- Returned the middle node.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of nodes in the linked list
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    // Function to find the middle node of a linked list
    public ListNode middleNode(ListNode head) {
        
        // Calculating the length of the linked list
        int l = length(head);
        int i = 0;
        
        // Traversing to the middle node
        while( i < l/2){
            head = head.next;
            i++;
        }
        
        // Returning the middle node
        return head;
    }

    // Function to calculate the length of a linked list
    static int length(ListNode h){
        int l = 0;
        
        // Traversing the linked list and count the nodes
        while( h != null){
            l++;
            h = h.next;
        }
        
        // Returning the length
        return l;
    }
}
```