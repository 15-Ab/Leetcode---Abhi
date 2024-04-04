#🎉 Special Day Greetings on the 4th! 🎉

##### Today, the 4th, holds a special significance for me, and I want to take a moment to share my gratitude with all of you who visit this GitHub repository. Your presence here makes this community vibrant and inspiring.

##### Thank you for being part of this journey. Here's to today and all the wonderful possibilities it brings !

# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 04-04-24 [Problem Link](https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/description/?envType=daily-question&envId=2024-04-04)
## 1614. Maximum Nesting Depth of the Parentheses

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
- I aim to find the maximum depth of nested parentheses in a given string.
# Approach
<!-- Describe your approach to solving the problem. -->
   - I initialized two variables, `jawab` and `khula`, to keep track of the maximum depth and current depth, respectively.
   - Iterated through each character `c` in the string `s`.
   - If `c` is an opening parenthesis '(', incremented `khula` and update `jawab` to the maximum of its current value and `khula`.
   - If `c` is a closing parenthesis ')', decremented `khula`.
   - Finally, returned `jawab` as the maximum depth of parentheses.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : length of the given string
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  public int maxDepth(String s) {
    
        // Initialize variables
        int jawab = 0; // Store the maximum depth found so far
        int khula = 0; // Keep track of the current depth

        // Iterate through each character in the string
        for (final char c : s.toCharArray()){
            // If the character is an opening parenthesis
            if (c == '('){
                khula++; // Incrementing the current depth
                jawab = Math.max(jawab, khula); // Updating maximum depth if necessary
            }
            // If the character is a closing parenthesis
            else if (c == ')'){
                khula--; // Decrementing the current depth
            }
        }
        // Returning the maximum depth found
        return jawab;
    }
}
```