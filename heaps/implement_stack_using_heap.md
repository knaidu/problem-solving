# Implement stack using heap

## Solution
- Use a max heap, let the ordering be based on insertion order
- For eg, first element gets order 1, next element gets order 2, keep a running count of insertion order
- For pop, extract max from the heap and it will be the most recent element inserted

## Code
```ruby
class HeapElement
    attr_accessor :data, :count

    def initialize(data, count)
        @data = data
        @count = count
    end
end

def comparator_function(element1, element2)
    element1.data < element2.data
end

class Stack
    attr_accessor :max_heap, count

    def initialize()
        max_heap = MaxHeap.new(comparator_function)
        count = 0
    end

    def push(num)
        @count += 1
        heap_element = HeapElement.new(num, count)
        max_heap.insert(heap_element)
    end

    def pop()
        heap_element = max_heap.extract_max

        heap_element.data
    end
end
```

## Complexity
- Time: O(log k) for push, where k is the number of elements already in the stack,
  O(1) for pop.
- Space: O(2k) for storing the elements in the heap and their associated ordering
