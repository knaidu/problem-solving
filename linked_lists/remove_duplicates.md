# Remove duplicates
Given a strted linked list, remove duplicates from them

## Example
```
Input list: 1,1,1,1,1,2,2,2,2,2,3,4,5
Output list: 1,2,3,4,5
```

## Solution
- Traverse the list and keep current and next pointers,
- Compare current with the next pointers and delete them if duplicate, if not move the current pointer to the next node

## Code
```ruby
def remove_duplicates
    return if @head.next.nil?

    prev = @head
    curr = prev.next

    while curr != nil
      if prev.data == curr.data
        prev.next = curr.next
      else
        prev = curr
      end

      curr = curr.next
    end
  end
```

## Time complexity
O(n) since we're doing a single pass over the linked list
