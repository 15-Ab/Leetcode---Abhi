# 🎉 Happy Holi, GitHub Friends ! 🌈🎨

## Wishing you a colorful and joyful Holi celebration ! 🥳 May your coding adventures be as vibrant and delightful as the festival itself. Thanks for stopping by my repo ! 💻🌟

## Happy Holi from me to you ! 🎊🎉

# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 26-03-24 [Problem Link](https://leetcode.com/problems/first-missing-positive/description/?envType=daily-question&envId=2024-03-26)
## 41. First Missing Positive

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Simply sort, then look for positive numbers.

# Approach
<!-- Describe your approach to solving the problem. -->
- Sorted the array ( used java collection sorting method which uses $n*log(n)$ time complexity so no issue)
- looked for positive numbers starting with 1, if found then searched next number ( 2, then 3, then 4...) 
- as array is sorted , no issue in arrangement of numbers
- the last positive number not found will be the answer

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(n log n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ :  length of the input array `nums`
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    // Method to find the first missing positive integer in the given array
    public int firstMissingPositive(int[] nums) {

        // Initializing the variable to store the potential missing positive integer
        int p = 1;

        // Sorting the array to simplify the search process
        Arrays.sort(nums);

        // Iterating through the array to find the first missing positive integer
        for (int i = 0; i < nums.length; i++) {
          
            // Checking if the current element matches the potential missing positive integer
            if (nums[i] == p) {
                // If it matches, incrementing the potential missing positive integer
                p++;
            }
        }

        // Returning the first missing positive integer found
        return p;
    }
}

```