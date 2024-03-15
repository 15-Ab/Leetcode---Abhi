# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 15-03-24 [Problem Link](https://leetcode.com/problems/product-of-array-except-self/description/?envType=daily-question&envId=2024-03-15)
## 238. Product of Array Except Self

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Given an array `nums` of integers, we are tasked with finding an array `jawab` such that `jawab[i]` is equal to the product of all the elements of `nums` except `nums[i]`.

# Approach
<!-- Describe your approach to solving the problem. -->
**Prefix Product Calculation** :
   - I first calculated the product of all elements to the left of each element `nums[i]` and stored it in the `jawab` array.
   - I initialized `jawab[0] = 1` and then iterate through the array from index 1 to `nums.length - 1`. For each index `i`, `jawab[i]` is assigned the product of all elements to the left of `nums[i]`.

**Suffix Product Calculation** :
   - I then calculated the product of all elements to the right of each element `nums[i]`, multiplying it with the corresponding value in the `jawab` array.
   - I initialized a variable `s = 1` and iterated through the array from right to left (index `nums.length - 1` to 0). For each index `i`, I multiplied `jawab[i]` with `s` and updated `s` by multiplying it with `nums[i]`.

**Final Result** :
   - After both prefix and suffix products are calculated and combined, the `jawab` array contained the desired product of all elements except `nums[i]` for each index `i`.
   - I returned the `jawab` array as the final result.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : length of the input array
- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    
    // Static variable to store the result
    static int[] jawab;

    // Method to calculate product of array except self
    public int[] productExceptSelf(int[] nums) {
        
        // Initializing the result array
        jawab = new int[nums.length];
        // Set the initial value of the first element in the result array to 1
        jawab[0] = 1;

        // Calculating product of elements to the left of current element
        for (int i = 1; i < nums.length; i++) {
            jawab[i] = jawab[i - 1] * nums[i - 1];
        }

        // Initializing a variable to store product of elements to the right of current element
        int s = 1;
        // Calculating product of elements to the right of current element and update result array
        for (int i = nums.length - 1; i >= 0; i--) {
            jawab[i] *= s;
            s *= nums[i];
        }

        // Returning the final result array
        return jawab;
    }
}
```