# Most visited page
Given a log file that contains the a number of entries, each line lists the page id which indicates it was visited.

## Solution
- Process each line and keep track of the count per page. Use a bst to store the actual count so that it preserves the sorted order and is easy to find the top k pages once all pages have been processed
- Each node of the BST contains count, use a hash table to store the link between page and its count
- Update the count each time a line is read, 
- Once all the pages have been read, to compute the k largest on the BST, first find the max (O(log n)) then use the pre-decessor function k-1 times to find the k most visited pages