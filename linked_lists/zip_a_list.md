# Zip a list
The zip of a list is creating a new list by having 2 pointers one from the start and one from the end and picking one node each and merging into a new list.

## Example
```
List: 1,2,3,4,5,6
Zip:  1,6,2,5,3,4
```

## Solution
- Split the list in the middle, into 2 lists
    ```ruby
    def split
    slow = @head
    fast = @head
    prev = slow

    while slow && fast && fast.next
      prev = slow
      slow = slow.next
      fast = fast.next.next
    end

    prev.next = nil
    slow
  end
    ```
- Reverse the second list
    ```ruby
    def reverse(head)
        puts 'Reversing ..'

        return nil if head.nil?
        return head if head.next.nil?

        if head.next.next.nil?
          prev = head
          curr = prev.next
          curr.next = prev
          prev.next = nil
          head = curr
          return head
        end

        prev = head
        curr = prev.next
        fwd = prev.next.next
        prev.next = nil

        while fwd.next != nil
          curr.next = prev
          prev = curr
          curr = fwd
          fwd = fwd.next
        end

        fwd.next = curr
        curr.next = prev

        fwd
    end
    ```
- Now merge the 2 lists
    ```ruby
    def merge_list(first, second)
        return second if first.nil?
        return first if second.nil?

        head = first
        curr = first
        first = first.next

        while(first && second)
          curr.next = second
          second = second.next
          curr = curr.next
          curr.next = first
          first = first.next
          curr = curr.next
        end

        if first
          curr.next = first
        elsif second
          curr.next = second
        end

        head
    end
    ```
- At a high level zip function looks like this
    ```ruby
    def zip
        return if @head.next.nil?
        return if @head.next.next.nil?

        first = @head
        second = split
        second = reverse(second)

        @head = merge_list(first, second)
    end
    ```

## Time complexity
- O(n) to split
- O(n) to reverse
- O(n) to merge
- Overall O(n)

