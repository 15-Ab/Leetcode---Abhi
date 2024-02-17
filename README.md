# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 17-02-24 [Problem Link](https://leetcode.com/problems/furthest-building-you-can-reach/description/?envType=daily-question&envId=2024-02-17)
## 1642. Furthest Building You Can Reach

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
This problem involved finding the furthest building that can be reached with a given number of bricks and ladders. To maximize the distance, I wanted to use ladders for the steepest climbs and save bricks for smaller climbs.

# Approach
<!-- Describe your approach to solving the problem. -->
**Priority Queue for Heights Difference :**
- Used a priority queue (min-heap) to keep track of the differences in heights between consecutive buildings.
- This helped in efficiently selecting the steepest climbs.

**Iterated Through Buildings :**
- Iterated through the buildings, calculating the height difference between consecutive ones.
- If the difference is non-positive, moved to the next building as no resources are needed for descending.

**Used Ladders for Steeper Climbs :**
- If the height difference is positive, added it to the priority queue.
- If the size of the priority queue exceeded the number of ladders available, it means I need to use bricks. Polled out the smallest height difference from the queue and subtracted it from available bricks.

**Checked Brick Availability :**
- After subtracting the bricks, if the bricks become negative, returned the current index as it indicated that the remaining buildings cannot be reached with the available resources.

**Retured the Furthest Reachable Building :**
- If the iteration completed without returning, all buildings can be reached. Returned the index of the last building.

My approach ensured efficient utilization of ladders for steeper climbs and used bricks only when necessary, allowing for the furthest possible reach with the given resources.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(n*logk)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : length of `heights` array

$k$ :  number of ladders ( given )
- Space complexity : $O(k)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    // Priority Queue to store the height differences
    static Queue<Integer> mH;
    
    // Variable to store the current height difference
    static int antr;
    
    // Main method to find the furthest building
    public int furthestBuilding(int[] heights, int bricks, int ladders) {
        
        // Initializing the priority queue
        mH = new PriorityQueue<>();
        
        // Iterating through the heights array
        for (int i = 0; i < heights.length - 1; i++) {
            
            // Calculating the height difference between consecutive buildings
            antr = heights[i + 1] - heights[i];
            
            // If the height difference is non-positive, continuing to the next iteration
            if (antr <= 0) {
                continue;
            }
            
            // Adding the height difference to the priority queue
            mH.offer(antr);
            
            // If the size of the priority queue exceeds the number of ladders available,
            // subtracting the smallest height difference from bricks
            if (mH.size() > ladders) {
                bricks -= mH.poll();
            }
            
            // If bricks become negative, returning the current index
            if (bricks < 0) {
                return i;
            }
        }
        
        // If all buildings can be reached, returning the last index
        return heights.length - 1;
    }
}
```