# Count number of inversions 
Given an unsorted array, count the number of inversions.

## Solution
- Use the merge sort algorithm and enhance it with the inversion count
- In the merging step, count inversions
    - if value in a > value in b, then inversions = a.end - a_index  
- Repeat this until the entire array is merged
