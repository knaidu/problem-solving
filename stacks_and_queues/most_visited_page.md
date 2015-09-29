# Most visited page in a window
You are given a log file containing (page name, visit timestamp) pair and a window size. For every window find the most visited page when the window advances by 1 until end of the log file. (Breaking ties by oldest)

## Example
Input: (g,1)(a,2)(t,3)(t,6)(a,7)(a,11), window size: 4 
Output: g, g, g, t, t, a

## Solution
- A window pattern translates to using a queue
- Use a queue for storing the page,visit pairs
    - When a new entry is seen, enqueue it to the tail, and dequeue all the entries from the head that are outside the window, example when a,11 is enqueued, dequeue all entries with timestamp less than 11-4 (window size)
- Now to keep track of the most visited use a hash table + BST combination
    - Increment/decrement the has table value on enqueue/dequeue operation on the queue
    - Follow this with an update to the BST (remove corresponding node, add new node with updated value)
- To report the most visited page within a window, return the max value in the BST

## Complexity
- Time: O(n) to enqueue and dequeue from queue. O(n log n) to update the BST, O(log n) to find the max, therefore overall complexity O(n log n)
- Space: O(n) for the queue, O(n) for the hash table, and O(n) for the BST