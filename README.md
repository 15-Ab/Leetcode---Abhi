# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 05-02-24 [Problem Link](https://leetcode.com/problems/first-unique-character-in-a-string/description/)
## 387. First Unique Character in a String

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal of my code is to find the index of the first non-repeating character in a given string `s`.

# Approach
<!-- Describe your approach to solving the problem. -->
**Counted Frequency :** 
   - Created a HashMap (`m`) to store the frequency of each character in the string.
   - Iterated through the string and count the frequency of each character using the HashMap.

**Founded First Non-Repeating Character :**
   - Iterated through the string again.
   - For each character, checked its frequency in the HashMap.
   - If the frequency is 1, returned its index.
   
**Helper Function (`index`) :**
   - A helper function is used to find the index of a specific character in the string.

**Returned -1 if No Non-Repeating Character :**
   - If no non-repeating character is found, returned -1.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ :  length of the input string `s`
- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    
    public int firstUniqChar(String s) {
        // HashMap to store the frequency of each character in the string
        HashMap<Character, Integer> m = new HashMap<>();
        
        // Counting the frequency of each character and storing in the HashMap
        for (int i = 0; i < s.length(); i++) {
            m.put(s.charAt(i), m.getOrDefault(s.charAt(i), 0) + 1);
        }
        
        // Iterating through the string to find the first non-repeating character
        for (char c : s.toCharArray()) {
            if (m.get(c) == 1) {
                // If found, returning the index using the helper function
                return index(s, c);
            }
        }
        
        // If no non-repeating character is found, returning -1
        return -1;
    }
    
    // Helper function to find the index of a specific character in a string
    static int index(String s, char c) {
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == c) {
                return i;
            }
        }
        // If the character is not found, returning -1 ( but this will not happen as character is present for sure )
        return -1;
    }
}
```