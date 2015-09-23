# Sliding window max
Given an array of values and a sliding window size, report the max at each step of the sliding window as we pass over all the values in the array.

## Solution
- This calls for a queue with max
- When we advance the window, enqueue the new element into the max_queue and dequeue from the max_queue
- Report 