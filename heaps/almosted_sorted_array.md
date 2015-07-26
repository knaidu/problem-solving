# Almosted sorted array
Given ar array that is almost sorted, where each number is at most k positions away from its final
place in the sorted array, sort this array effeciently.

## Example
```
Input: 3, -1, 2, 6, 4, 5, 8
k = 3
```

## Solution
- Since we know each element is at most k positions away from its final place, it implies that
  for a given number we only need to consider k elements around it, other elements do not impact
  its position
- Use a min heap and insert k elements to begin with, then extract one and insert the next form
  the array, until all elements are exhausted.

## Code
```ruby
def almost_sorted(arr, k)
    return arr if k == 0 # Already sorted

    min_heap = MinHeap.new
    sorted_result = []

    # Insert k elements into the heap
    i = 0
    while i < k
        min_heap.insert(arr[i])
        i += 1
    end

    # Process each element form the array
    while i < n
        sorted_result << min_heap.extract_min
        min_heap.insert(arr[i])
        i += 1
    end

    # Extract remaining elements form the heap
    while !min_heap.empty?
        sorted_result << min_heap.extract_min
    end

    sorted_result
end
```

## Complexity
- Time: O(n log k), n elements to process log k per element to extract form min heap
- Space: O(k), because we hold k elements in the heap while processing the array.
