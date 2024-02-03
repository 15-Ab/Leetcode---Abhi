# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 03-02-24 [Problem Link](https://leetcode.com/problems/partition-array-for-maximum-sum/description/?envType=daily-question&envId=2024-02-03)
## 1043. Partition Array for Maximum Sum

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
This problem involves partitioning an array into subarrays and finding the maximum sum of these subarrays. To efficiently solve this problem, I have used dynamic programming to keep track of the maximum sum for each subarray ending at a given index.


# Approach
<!-- Describe your approach to solving the problem. -->
- Initialized a static array `jawab` to store the maximum sum for each subarray ending at index `i`.
- Iterated through the array from index 1 to the length of the array.
  - Initialized a variable `b` to the minimum integer value to store the maximum value in the current subarray.
  - Iterated through the subarray lengths up to 'k' or 'i', whichever is smaller.
    - Updated `b` to the maximum value in the current subarray.
    - Updated the maximum sum for the current subarray ending at index `i` using the formula `jawab[i] = max(jawab[i], b * j + jawab[i - j])`.
- Returned the maximum sum after partitioning the array, which is stored in `jawab[arr.length]`.

My dynamic programming approach efficiently calculates the maximum sum for each subarray, considering previous results to avoid redundant computations and achieve an optimal solution.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(l*k)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$l$ : length of the input array `arr`

$k$ : given
- Space complexity :  $O(l)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    // Static array to store the maximum sum for each subarray ending at index i
    static int[] jawab;
    
    // Variable to store the length of the subarray considered for partitioning
    static int b;
    
    // Method to calculate the maximum sum after partitioning the array
    public int maxSumAfterPartitioning(int[] arr, int k) {
        // Initializing the static array to store results
        jawab = new int[1 + arr.length];

        // Iterating through the array
        for (int i = 1; i <= arr.length; i++) {
            // Initializing b to the minimum integer value
            b = Integer.MIN_VALUE;
            
            // Iterating through the subarray lengths up to 'k' or 'i', whichever is smaller
            for (int j = 1; j <= Math.min(i, k); j++) {
                // Updating 'b' to the maximum value in the current subarray
                b = Math.max(b, arr[i - j]);
                
                // Updating the maximum sum for the current subarray ending at index i
                jawab[i] = Math.max(jawab[i], b * j + jawab[i - j]);
            }
        }
        // Returning the maximum sum after partitioning the array
        return jawab[arr.length];
    }
}

```
