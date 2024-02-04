# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

##### Today is 4, a very auspicious day for me. You know, some dates are such that you're bound to keep them in your grateful diary, for me 4 is that day. No words can ever express how grateful I am to god for that feeling. It's a request to all you guys reading my repository - Life is full of ups and downs, happy in a momment and pain in another, you cann't avoid any of these, so remember who you are and keep faith in yourself as I do.
Enjoy my solution and keep coding :)

## Always here to assist you guys.

## Today's 04-02-24 [Problem Link](https://leetcode.com/problems/minimum-window-substring/description/?envType=daily-question&envId=2024-02-04)
## 76. Minimum Window Substring

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My code is aimed to find the minimum window substring in string `s` that contains all characters of string `t`. I utilized a sliding window approach to efficiently identify the minimum window.

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialization :**
   - I maintained an array `charCount` to store the count of characters in the ASCII range (128 characters).
   - Initialized `requiredChars` to the length of string `t`, representing the number of characters required to form the window.
   - Set `bestLeftIndex` to -1, indicating no valid window found yet.
   - Initialized `minWindowSize` to a value greater than the length of string `s`.

**Character Counting :**
   - Populated the `charCount` array with counts of characters in string `t`.

**Sliding Window :**
   - Used two pointers, `left` and `right`, to define a window.
   - Iterated through the string `s` with the right pointer (`right`).
   - Updated `charCount` and `requiredChars` based on the character at the right pointer.
   - Checked if the current window contains all required characters.
   - If the condition is satisfied, update the `bestLeftIndex` and `minWindowSize`.
   - Moved the left pointer (`left`) to shrink the window, updating `charCount` and `requiredChars` accordingly.

**Result :**
   - The result is the minimum window substring found based on `bestLeftIndex` and `minWindowSize`.

My sliding window approach efficiently explores all possible windows, ensuring that the minimum window containing all characters of `t` is identified.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(s + t)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$s$ : length of string `s`

$t$ : length of string `t`
- Space complexity : $O(1)$ (as the size of the `charCount` array is constant)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public String minWindow(String s, String t) {
        int[] charCount = new int[128];  // Array to store the count of characters
        int requiredChars = t.length();  // Number of characters required to form the window
        int bestLeftIndex = -1;          // Starting index of the best window
        int minWindowSize = s.length() + 1;  // Minimum window size

        // Initializing charCount array with counts of characters in string 't'
        for (char c : t.toCharArray())
            ++charCount[c];

        // Sliding window approach
        for (int left = 0, right = 0; right < s.length(); ++right) {
            // Update charCount and requiredChars based on the character at the right pointer
            if (--charCount[s.charAt(right)] >= 0)
                --requiredChars;

            // Checking if the window contains all required characters
            while (requiredChars == 0) {
                // Updating the best window if the current window is smaller
                if (right - left + 1 < minWindowSize) {
                    bestLeftIndex = left;
                    minWindowSize = right - left + 1;
                }

                // Moving the left pointer and update charCount and requiredChars
                if (++charCount[s.charAt(left++)] > 0)
                    ++requiredChars;
            }
        }

        // Returning the minimum window substring or an empty string if no such window exists
        return bestLeftIndex == -1 ? "" : s.substring(bestLeftIndex, bestLeftIndex + minWindowSize);
    }
}

```