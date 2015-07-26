# Closest stars
Given an array of integers that consists co-ordinates of n starts, find the k closest starts
to earth assuming earch is at co-ordinate 0,0.

## Solution
- Evaluate each co-ordinate, compute the distance from earth to that start
- Insert the distance into a max-heap, each time a new distance is added remove the max element
  from the heap.
- The goal is after n elements are processed the largest n-k elements woould have been removed
  from the heap and the smalles k elements will remain in the heap
- For this problem let's assume the relative distances have been calculated and given in the array

## Code
```ruby
def k_closest_elements(arr, k)
    max_heap = MaxHeap.new
    i = 0

    # Insert k elements into max_heap
    while i < k
        max_heap.insert(arr[i])
        i += 1
    end

    # Insert rest of the elements by removing 1 element from max_heap
    while i < n
        max_heap.extract_max
        max_heap.insert(arr[i])
        i += 1
    end

    # Extract the remaining k elements from max_heap and return in an array
    k_closest_in_sorted_order = []
    while !max_heap.empty?
        k_closest_in_sorted_order.unshift(max_heap.extract_max)
    end

    k_closest_in_sorted_order
end
```

## Complexity
- Time: O(n * log k), processing n elements, with k in the heap at any point of time
- Space: O(k) heap size
