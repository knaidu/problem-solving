# K largest in Heap
Given a max heap represented as an array, without modifying the heap or array find out the
k-largest elements in it.

## Solution
- Since we are not allowed to modify the heap, create another heap and insert elements into it
  until we have extracted k largest elements from the new heap
- For each extraction insert the node's children, using 2n and 2n+1 to index left and right child

## Code
```ruby
# Function used for ordering elements in the heap
def comparator_function(element1, element2)
    arr[element1] > arr[element2]
end

# Method to determine if x is a valid index for arr
def valid(arr, x)
    return false if arr[x].nil?
    return false if x >= arr.size
    return true
end

# Extract k largest elements from the heap
def k_largest(arr, k)
    max_heap = MaxHeap.new
    result = []

    # Initialize with the largest element, i.e. first element from array
    max_heap.insert(0)

    Extract and insert back until we have extracted k elements
    while k > 0
        i = max_heap.extract_max
        result << arr[i]
        max_heap.insert(2*i) if valid(2*i)
        max_heap.insert(2*i + 1) if valid(2*i+1)
        k += 1
    end

    result
end
```

## Complexity
- Time: O(k log k) extracting k elements
- Space: O(k) for holding k elements in the heap
