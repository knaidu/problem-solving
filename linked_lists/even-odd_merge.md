# Even-odd merge
Write a function that takes a singly linked list L, and reorders the elements of L so that the new list represents even-odd(L). Your function should use 0(1) additional storage. The only field you can change in a node is next.

## Examples
```
Input: 1,2,3,4,5,6
Output: 2,4,6,1,2,3
```

## Solution
The meat of this problem is pointer manipulation.
- Start with odd and even pointers
  ```ruby
    odd_ptr = @head
    even_ptr = @head.next

    first_odd_ptr = @head   // head of the odd list
    result_ptr = @head.next // the merged list
  ```

- Traverse the list and update the odd pointer to point to the next odd node and even pointer to point to the next even node, essentialy breaking the list into 2 - odd list and even list
  ```ruby
  while even_ptr != nil || odd_ptr != nil
      odd_ptr.next = odd_ptr.next.next
      odd_ptr = odd_ptr.next
      if even_ptr.next
        even_ptr.next = even_ptr.next.next
        even_ptr = even_ptr.next
      else
        break
      end
    end
  ```
- Now attach the start of the odd list to the end of the even list
  ```ruby
   even_ptr.next = first_odd_ptr
   return @head = result_ptr
  ```

## Code
```ruby
  def even_odd_merge
    odd_ptr = @head
    even_ptr = @head.next

    first_odd_ptr = @head
    result_ptr = @head.next

    while even_ptr != nil || odd_ptr != nil
      odd_ptr.next = odd_ptr.next.next
      odd_ptr = odd_ptr.next
      if even_ptr.next
        even_ptr.next = even_ptr.next.next
        even_ptr = even_ptr.next
      else
        break
      end
    end

    even_ptr.next = first_odd_ptr
    return @head = result_ptr
  end
end

l = LinkedList.new([1,2,3,4,5,6,7,8])
l.print_list(l.head)
l.even_odd_merge
l.print_list(l.head) #=> 2,4,6,8,1,3,5,7

```
## Time complexity
O(n) since we traversing the list only once
