# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 04-01-24 [Problem Link](https://leetcode.com/problems/minimum-number-of-operations-to-make-array-empty/description/)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
- Frequency Count :
- - The code starts by creating a HashMap (m) to store the frequency of each number in the given array. This is crucial for determining how many times each number appears in the array.

- Divisibility by 3 :
- - The primary goal is to minimize the operations needed to make all elements 0. The code examines the frequency of each number and calculates the minimum operations required based on certain conditions.

# Approach
<!-- Describe your approach to solving the problem. -->
- HashMap for Frequency :
- - Iterate through the input array (nums).
Use a HashMap (m) to store the frequency of each number in the array.
- Calculate Operations :
- - Iterate through the keys of the HashMap (m).
- - For each key 'k' observe it's occurence :
- - - If the occurrence is 1, return -1 (as it's not possible to make it 0 by subtracting 2 or 3).
- - - if occurence of number is divisible by 3, total operations = occurences/3 
- - - if occurence of number is of form 3*n + 1, let's try to break it down
- - - - 3*n + 1 = 3*(n-1) + 4 = 3*(n-1) + 2*(2) -> n-1+2 operations = n+1 
- - - if occurence of number is of form 3*n + 2, let's try to break it down
- - - - 3*n + 2 = 3*(n) + 2*(1) -> n+1 operations 
- Return Result :
- - Return the total number of operations needed to make all numbers in the array divisible by 3. 
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $$O(l)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $$O(u)$$

$$l$$ : size of array
$$u$$ : number of unique letters in array
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public int minOperations(int[] nums) {
        boolean haveone = false;
        HashMap<Integer, Integer> m = new HashMap<>();
        for( int i = 0; i < nums.length; i++){
            m.put( nums[i], m.getOrDefault(nums[i], 0) + 1);
        }
        int operations = 0;

        // if occurence of number is divisible by 3, total operations = occurences/3 
        // if occurence of number is of form 3*n + 1, let's try to break it down
        //  3*n + 1 = 3*(n-1) + 4 = 3*(n-1) + 2*(2) -> n-1+2 operations = n+1 
        // if occurence of number is of form 3*n + 2, let's try to break it down
        //  3*n + 2 = 3*(n) + 2*(1) -> n+1 operations 
  
        for( int k : m.keySet()){
            if( m.get(k) == 1){
                return -1;
            }
            if( m.get(k) % 3 == 0){
                operations += m.get(k)/3;
            }
            else{
                operations += m.get(k)/3 + 1;
            }
        }
        return operations;
    }
}
```
