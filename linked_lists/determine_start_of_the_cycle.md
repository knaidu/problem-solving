# Determine start of the cycle
Given a linked list with a cycle in it, detect the cycle and find the start node of the cycle

## Solution
Find the cycle using fast ptr slow ptr approach
- Set both pointers to the head of the list
- Increment fast pointer by 2 and slow pointer by 1 each time
- If we hit the end of the list then the list doesn't have a cycle
- If fast ptr and slow ptr point to the same node then we have detected a cycle in the list

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

Determine start of the cycle
- Once the loop is detected, freeze the fast ptr and increment the slow ptr by 1 until it meets the fast ptr, this will tell us the length of the loop
- Set the slow ptr to the head and increment the fast pointer until it is loop_length nodes away from the head
- Now increment both pointers by 1 until they meet again, that will be the node at which the cycle starts

  ```ruby
  slow_ptr = head
  fast_ptr = head

  // determined by freezing fast ptr
  // and incrementing slow ptr inside the loop
  loop_length = x

  while loop_length != 0
    fast_ptr = fast_ptr.next
    loop_length -= 1
  end

  while slow_ptr != fast_ptr
    slow_ptr = slow_ptr.next
    fast_ptr = fast_ptr.next
  end

  return slow_ptr
  ```

## Time compelxity
O(n)
