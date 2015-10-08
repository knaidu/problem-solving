# Reverse a list
Given a singly linked list, reverse it and return the new head pointer.

## Solution
- Handle the case of one and two nodes upfront
    ```ruby
    return nil if @head.nil?
    return @head if @head.next.nil?

    if @head.next.next.nil?
      prev = @head
      curr = prev.next
      curr.next = prev
      prev.next = nil
      @head = curr
      return
    end
    ```
- If the list is longer than 3 nodes then start reversing them in a loop using prev, curr and fwd pointers
    ```ruby
    prev = head
    curr = prev.next
    fwd = curr.next
    prev.next = nil

    while fwd.next != nil
      curr.next = prev
      prev = curr
      curr = fwd
      fwd = fwd.next
    end

    fwd.next = curr
    curr.next = prev

    @head = fwd
    ```

## Time complexity
O(n) since we are traversing the list only once

## Variations
- Reverse only a sublist
- Use this reversing technique to test if the list has a cycle - after reversing if we end up at the original head then there is a cycle in the list

