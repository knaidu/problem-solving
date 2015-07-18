# Sort a stack
Given a stack that has elements in random order, sort it recursively
without explicitly using another stack.

## Solution
Sort
- Pop the top element
- recursively sort the stack, until its empty
- then insert popped element

Insert
- If stack is empty or top element is less than element to be inserted, then push element
- Else, pop the top of stack into f, and recursively insert e, and then push f onto the stack

## Code
```ruby
def sort_stack(s)
    if !s.empty?
        e = s.pop
        sort_stack(s)
        insert(e,s)
    end
end

def insert(s, e)
    if s.empty || s.top <= e
        s.push(e)
    else
        f = s.pop
        insert(s, e)
        s.push(f)
    end
end
```

## Complexity
Essentially we are creating another stack using recursion and re-inserting each element in its
right place using a simple insertion sort like technique. Therefore time complexity O(n^2).
