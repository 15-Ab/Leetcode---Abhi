# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 03=03-24 [Problem Link](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/?envType=daily-question&envId=2024-03-03)
## 19. Remove Nth Node From End of List

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal is to remove the Nth node from the end of a singly-linked list.

# Approach
<!-- Describe your approach to solving the problem. -->
- I initialized two pointers, `l` and `skip`, both pointing to the head of the linked list.
- Moved the `skip` pointer N nodes ahead. If it becomes null during this process, it means the length of the linked list is exactly N. In this case, return `head.next` as we need to remove the head.
- Moved both pointers until the `skip` pointer reaches the end of the linked list.
- Updated the `next` pointer of the node pointed by `l` to skip the Nth node from the end.
- Returned the modified head of the linked list..

My approach utilized two pointers to efficiently find and remove the Nth node from the end of the linked list.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(N)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $o(1)$
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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode l = head;   // Initializing a pointer 'l' to the head of the linked list
        ListNode skip = head; // Initializing a pointer 'skip' to the head of the linked list to track the skipped parts

        // Moving 'skip' pointer n nodes ahead
        for (int i = 0; i < n; i++) {
            skip = skip.next;
            
            // If 'skip' becomes null, it means the length of the linked list is exactly n,
            // and I need to remove the head. Return head.next in this case.
            if (skip == null) {
                return head.next;
            }
        }

        // Move both pointers until 'skip' reaches the end of the linked list
        while (skip.next != null) {
            skip = skip.next;
            l = l.next;
        }

        // Removing the nth node from the end by updating the 'next' pointer of the node before it
        l.next = l.next.next;

        // Returning the modified head of the linked list
        return head;
    }
}
```