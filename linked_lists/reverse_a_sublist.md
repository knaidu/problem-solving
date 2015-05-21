# Reverse a sublist
Given a linked list with head ptr, a start and an end pointer, reverse the sublist from start_ptr to end_ptr

## Examples

input list: 1, 2, 3, 4, 5, 6, 7, 8

start_ptr = 3

end_ptr = 6

output list: 1, 2, 3, **7, 6, 5, 4**, 8

## Solution
- Keep track of the node before start_ptr and after end_ptr to adjust pointers accordingly after reversing the sublist

    ```ruby
    after_end = end_ptr.next

    before_start = head
    while before_start.next != start_ptr
        before_start = before_start.next
    end
    ```
- Reverse the list from start_ptr until end_ptr

    ```ruby
    prev = start_ptr
    curr = start_ptr.next
    fwd = start_ptr.next.next

    // Point prev to
    prev.next = after_end

    while curr != end_ptr.next
        curr.next = prev
        prev = curr
        curr = fwd
        fwd = fwd.next
    end

    // Adjust start and end of the lists accordingly
    before_start.next = prev
    start_ptr.next = curr
    ```

## Time complexity
O(n) since we're traversing the list only once
