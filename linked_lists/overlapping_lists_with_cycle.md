# Overlapping lists with cycle
Let hI and h2 be the heads of lists Ll and L2, respectively. Assume that L1 and L2 are may have cycles. Find if they are overlapping or not.

## Solution
- Determine if L1 has and L2 a cycle using fast_ptr-slow_ptr method
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

- If only one of them has a cycle then the lists cannot overlap
- Only if both the lists have cycles then they can overlap and in that case they both must have the same cycle of nodes.
- To determine if they have the same cycle, we must find the starting node of the cycle and verify its idential for both L1 and L2.
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

## Time complexity
O(n) for determining cycle in both lists
O(n) to determine start of cycle and confirming the lists overlap.
Overall complexity O(n).
