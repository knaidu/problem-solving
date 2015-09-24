# Sliding window max
Given an array of values and a sliding window size, report the max at each step of the sliding window as we pass over all the values in the array.

## Solution
- This calls for a queue with max
- When we advance the window, enqueue the new element into the max_queue and dequeue from the max_queue
- Report the max in the queue after each move

## Code
```ruby
def sliding_window(arr, sliding_window)
    return nil if arr.nil?
    
    max_queue = MaxQueue.new
    
    arr.each do |e|
        max_queue.enqueue(e)
        max_queue.dequeue if max_queue.size > sliding_window
        puts max_queue.max
    end
end

class MaxQueue
    attr_accessors :queue, :max_queue
    
    def initialize()
        queue = []
    end
    
    def enqueue(e)
        queue.enqueue(e)
        tail = max_queue.last
        if tail >= e
            max_queue.enqueue(e)
        else
            # Dequeue until tail is greater than element or queue becomes empty
            while tail < e && max_queue.size > 0
                max_queue.dequeue
            end
            max_queue.enqueue(e)
        end
    end
    
    def dequeue
        e = queue.dequeue
        if e == max_queue.first
            max_queue.dequeue
        end
        
        return e
    end
    
    def max
        max_queue.first
    end
end
```

## Time complexity
- O(n) to parse over the array moving the sliding window one step at a time