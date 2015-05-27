# Remove kth last element
Given a singly linked list and k, find and remove the kth element from the end

## Example
```
List: 1,2,3,4,5,6,7,8,9
k: 4
Output: 1,2,3,4,5,7,8,9
```

## Solution
- Use the tail_ptr technique to find the kth last element
    ```ruby
    tail = head
    curr = head
    count = 1

    while curr != nil && count < k
      curr = curr.next
      count += 1
    end

    while curr.next != nil
      curr = curr.next
      tail = tail.next
    end
    ```
- To delete and element, instead of having a prev pointer the easy way is to copy data from the next ptr and delete the next node

    ```ruby
    temp = tail.next
    tail.data = temp.data
    tail.next = temp.next
    ```

## Time complexity
- Single pass to find the kth last node
- O(1) to delete the kth node
