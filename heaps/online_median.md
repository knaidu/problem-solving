# Online median
Design an algorithm for computing the running median of a sequence of numbers.

## Solution
- Use a combination of min and max heap
- Smaller half would use a min heap and larger half would use a max heap
- The idea is to keep track of the "middle" 2 elements and then compute median among them
  depending on how many elements are before and after it in the hypothetical sorted array

## Code
```ruby
def online_median(integer_stream)
    min_heap = MinHeap.new
    max_heap = MaxHeap.new

    while x = integer_stream.get
        # First element
        min_heap.insert(x) if min_heap.empty?

        # Insert in max or min heap
        if x > min_heap.min
            min_heap.insert(x)
        else
            max_heap.insert(x)
        end

        # Balance the heaps
        if max_heap.size - min_heap.size > 1
            min_heap.insert(max_heap.extract_max)
        else
            max_heap.insert(min_heap.extract_min)
        end

        # Print median
        if min_heap.size == max_heap.size ?
            median = (min_heap.min + max_heap.max) / 2
        els
            median = min_heap.min
        end
    end
end
```

## Complexity
- Time: O(log n) for inserting into either heap, extract is O(1).
