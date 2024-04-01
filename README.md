# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 01-04-24 [Problem Link](https://leetcode.com/problems/length-of-last-word/description/?envType=daily-question&envId=2024-04-01)
## 58. Length of Last Word

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
To find the length of the last word in the given string, I need to identify and isolate the last word. This involves trimming any leading or trailing spaces from the string and then locating the last space character to determine where the last word begins. Once I have isolated the last word, I can calculate its length and return it.

# Approach
<!-- Describe your approach to solving the problem. -->
**Trim the string** : Remove dleading and trailing spaces from the input string.

**Finded the last space index** : Determined the index of the last space character in the trimmed string.

**Calculated the length of the last word** : Subtracted the index of the last space from the length of the trimmed string to find the length of the last word.

**Returned the length of the last word** : Provided the calculated length as the output.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : length of the string
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public int lengthOfLastWord(String s) {
        // Trimming the string to remove leading and trailing spaces
        s = s.trim();
        
        // Finding the index of the last space character
        int lastSpaceIndex = s.lastIndexOf(' ');
        
        // Calculating the length of the last word
        int lengthOfLastWord = s.length() - lastSpaceIndex - 1;
        
        // Returning the length of the last word
        return lengthOfLastWord;
    }
}
```