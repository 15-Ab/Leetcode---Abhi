# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 05-03-24 [Problem Link](https://leetcode.com/problems/minimum-length-of-string-after-deleting-similar-ends/description/?envType=daily-question&envId=2024-03-05)
## 1750. Minimum Length of String After Deleting Similar Ends

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal is to find the minimum length of a string after repeatedly removing the same character from both ends until the string is no longer symmetric.

# Approach
<!-- Describe your approach to solving the problem. -->
- I initialized two pointers, `leftIdx` and `rightIdx`, at the beginning and end of the string, respectively.
- Used a while loop to iterate while `leftIdx` is less than `rightIdx` and the characters at these indices are equal.
- Inside the loop :
   - Stored the current character at `leftIdx` in the variable `currentChar`.
   - Moved `leftIdx` to the right until a different character is encountered.
   - Moved `rightIdx` to the left until a different character is encountered.
- Calculated and return the length of the remaining string by subtracting `leftIdx` from `rightIdx` and adding 1.

My algorithm efficiently reduced the length of the string by removing symmetric characters from both ends until no more symmetric characters are found.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)

# Complexity
- Time complexity : $O(s)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$s$ : length of the input string
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    
  // Method to find the minimum length
  public int minimumLength(String s) {
    // Initialize two pointers, leftIdx and rightIdx
    int leftIdx = 0;
    int rightIdx = s.length() - 1;

    // Iterating while the leftIdx is less than rightIdx and characters at these indices are equal
    while (leftIdx < rightIdx && s.charAt(leftIdx) == s.charAt(rightIdx)) {
      
      // Storing the current character
      final char currentChar = s.charAt(leftIdx);

      // Moving leftIdx to the right until a different character is encountered
      while (leftIdx <= rightIdx && s.charAt(leftIdx) == currentChar){
        leftIdx++;
      }

      // Moving rightIdx to the left until a different character is encountered
      while (leftIdx <= rightIdx && s.charAt(rightIdx) == currentChar){
          rightIdx--;
      }
          
    }

    // Returning the calculated minimum length
    return rightIdx - leftIdx + 1;
  }
}

```