# Max stack

Implement a stack that in addition to pop and push, provides a max function, that returns the max element in the stack.

## Example
```
stack.push(2,1,100,3,500)
stack.max #=> 500
stack.pop
stack.max #=> 100
```

## Algorithm
Trick is to use an additional stack that keeps track of the max seen so far
- On push, push element to max-stack only if its greater than the last element in max-stack
- On pop, remove element from max stack only if its the same as the one being removed from the stack

## Code
```ruby
class StackWithMax
  def initialize
    @stack = []
    @max_stack = []
  end

  def push(value)
    @stack.push value
    if @max_stack.empty?
      @max_stack.push(value)
    elsif @max_stack.last < value
      @max_stack.push(value)
    end
  end

  def pop
    value = @stack.pop
    if @max_stack.size != 0 && @max_stack.last == value
       @max_stack.pop
    end

    value
  end

  def max
    @max_stack.last
  end
end
```

## Time complexity
Since we're doing all the work during push and pop, max operation is O(1). The push and pop operation remain the same as regular stack i.e. O(1)
