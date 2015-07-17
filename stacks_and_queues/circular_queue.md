# Circular Queue
Build a circular queue

## Solution
- Use an array with front and back pointers, and max size
- Insert elements at the back, remove elements from front
- Circle around using % max_size

## Code
```ruby
class CircularQueue
  attr_reader :queue, :front, :back, :size, :max_size

  def initialize(max_size)
    @queue = [0]*max_size #Initialize the queue to 0
    @front = 0
    @back = 0
    @size = 0
    @max_size = max_size
  end

  def insert(element)
    if @size < @max_size
      @queue[@back] = element
      @back += 1 % @max_size
      @size += 1
    else
      raise StandardError.new('Queue is full, cannot insert elements.')
    end
  end

  def remove
    if @size == 0
      raise StandardError.new('Queue is empty, no elements to remove.')
    else
      element = @queue[@front]
      @queue[@front] = 0
      @front += 1 % @max_size
      @size -= 1
      return element
    end
  end
end
```

## Complexity
- O(1) inserts and deletes
