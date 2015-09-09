# Count entries in an interval
Given a BST where each node is augmented with number of nodes under it, how would you find the number of nodes in a given interval

## Solution
- Find the leftmost node that is closest to the start_interval, 
- Compare the value and go left or right, if we fall off the tree at any point we should stop as thats the closest we can get to the value 
- While doing this each time we take the left child we leave the count unchanged, when we take the right child we add 1 + left children to the count
- Similarly find the right most node that is closest to the end_interval
- Now subtract this from the total number of nodes at the root to get the number of entries that are within the specified interval