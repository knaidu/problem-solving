# Test for palindromicity
Given a linked list, test if its a palindrome

## Example
```
1,2,3,4,5,6 => false
1,2,3,3,2,1 => true
1,2,1 => true
```

## Solution
- Use fast_ptr slow_ptr approach to traverse to the middle of the list, while traversing add the elements to the stack. We now have the first half of the elements in a stack.
- Now traverse towards the end of the list and compare each element with the popped element from the stack
- If we reach the end of the list and all elements are the same then we have a palindrome else we do not

## Code
```ruby
def is_palindrome
    return true if @head.next == nil

    if @head.next.next == nil
      return @head.data == @head.next.data
    end

    slow_ptr = @head
    fast_ptr = @head

    while fast_ptr != nil && fast_ptr.next != nil
      slow_ptr = slow_ptr.next
      fast_ptr = fast_ptr.next.next
    end

    # Move to the first node in the 2nd half of the list
    slow_ptr = slow_ptr.next

    data_stack = []

    while slow_ptr != nil
      data_stack.push(slow_ptr.data)
      slow_ptr = slow_ptr.next
    end

    slow_ptr = @head

    while !data_stack.empty?
      value = data_stack.pop
      if value != slow_ptr.data

        return false
      end
      slow_ptr = slow_ptr.next
    end

    return true
  end
```
