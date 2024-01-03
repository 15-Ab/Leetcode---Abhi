# Leetcode Daily Challenge Solutions

This is my attemp to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 03-01-24 [Problem Link](https://leetcode.com/problems/number-of-laser-beams-in-a-bank/solutions/?envType=daily-question&envId=2024-01-03)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Basic multiplication.
# Approach
<!-- Describe your approach to solving the problem. -->
- I kept track of number of '1' in a row
- Now iterated over every row of array 
- - counted the number of '1' in current row
- - number of beams will the product of current number of device and previous number of devices
- -  added the product to answer
- -  now, the current one will become the previous one to next row
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $$O(l)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$l$$ : length of array
- Space complexity : $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public int numberOfBeams(String[] bank) {
        int jawab = 0;      // to store answer
        int picheek = 0;    // to store number of '1' in previous state

        for( String r : bank){
            int ek = (int) r.chars().filter( g -> g == '1').count(); // counting the number of '1' in current row
            if( ek != 0){             // number of beams will the product of current number of device and previous number of devices
                jawab += picheek*ek; // adding the product to answer
                picheek = ek;        // now, the current one will become the previous one to next row
            }
        }
        return jawab;
    }
}
```
