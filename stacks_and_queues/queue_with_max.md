# Queue with max
Implement a queue that in addition to enqueue and dequeue operations provides a max function
to find the max element in the queue at any time.

## Solution
- Maintain another max_queue, head of that queue will be the max element
- When an element is enqueued
    - Check tail of max_queue, if tail is greater than element, then insert at tail
    - If tail is less than element, then remove from tail iteratively until max_queue
      is empty or tail element is greater than or equal to the element
- When an element is dequeued
    - Check if its same as max_queue's head, if it is then remove, else no action.

- Concept here is: max queue must contain elements in decreasing order, any element that will
  get dequeued before it gets a chance to become max must be removed from max queue

## Code
```ruby
class MaxQueue
    attr_reader :queue, :max_queue

    def enqueue(element)
        queue.push(element) # Insert at tail

        # Iteratively remove from max_queue until its empty
        # or tail element is greater than element
        while max_queue.last < element || !max_queue.empty?
            max_queue.pop
        end
        max_queue.push(element)
    end

    def dequeue
        element = queue.shift
        if max_queue.first == element
            max_queue.shift
        end

        element
    end

    def max
        max_queue.first
    end
end
```

## Complexity
- Time: O(n) enqueue in the worst case (due to iterative remove on max queue),
  O(1) dequeue, O(1) max operation.
- Space: O(n) additional space for max_queue.
- This algo is optimized for O(1) max, we can make appropriate tradeoffs depending
  on the priorities here.
