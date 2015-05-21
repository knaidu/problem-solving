# Cyclic right shift
Given a linked list, implement a cyclic right action on it.

## Solution
- For a cyclic right shift the last node of the list must be disconnected and re-attached to the start of the linked list
- Traverse to the last node, keeping track of the last but one node as well
- Make the last but one node the last node of the list, attach the last node to the head of the list and return the new head

## Code
```ruby
def cyclic_right_shift
    if @head.next.nil?
      return
    end

    prev = @head
    curr = @head.next

    while curr.next
      prev = curr
      curr = curr.next
    end

    prev.next = nil
    curr.next = @head
    @head = curr
  end
```

## Time complexity
O(n) since we traversed the list only once during the cyclic right shift operation

## Variation
Take in a number x and implement cyclic right shift action x times
