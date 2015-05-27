# Test for cycle
Given a linked list, test if it has a cycle in it, i.e the tail node does not point to nil, it points to another node in the list.

## Solution
Use the fast_ptr and slow_ptr method to detect if a cycle exists in the list

```ruby
def is_loop(head)
  return false if head == nil
  return false if head.ptr == nil

  slow_ptr = head
  fast_ptr = head
  fast_ptr = fast_ptr.ptr
  fast_ptr = fast_ptr.ptr

  while fast_ptr != nil && slow_ptr != nil do
    if slow_ptr == fast_ptr
      return true
    end

    slow_ptr = slow_ptr.ptr
    fast_ptr = fast_ptr.ptr
    fast_ptr = fast_ptr.ptr if fast_ptr != nil
  end

  return false
end
```

## Time complexity
O(n) since we are traversing the list only once
