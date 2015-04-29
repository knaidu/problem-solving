# Queue with 2 stacks
Implement a queue with two stacks so that each queue operations takes a constant amortized number of stack operations.

## Example
```
Q = [1,2,3,4]
Q.push(5)
Q = [1,2,3,4,5]
Q.pop # => 1
```

## Algorithm
1. Use stack 1 to push elements to and stack 2 to pop elements from.
2. When poping elemtns if stack 2 is empty then move elements from stack1 to stack 2
3. At this time the order gets reversed and when poped from stack 2 the order gets reversed once again thus giving us the FIFO order.

## Code
```ruby
class Queue
  def initialize
    @stack1 = []
    @stack2 = []
  end

  def push(value)
    @stack1.push(value)
  end

  def pop
    if @stack2.empty?
      move_elements
    end
    @stack2.pop
  end

  def is_full?(stack)
    stack.size == max_size
  end

  def move_elements
    while !@stack1.empty?
      @stack2.push(@stack1.pop)
    end
  end
end
```

## Time complexity
1. Push requires 1 operation
2. Pop requires 2 operations
3. Overall amortized complexity for push and pop is O(1)
