# Copy a postings list
You are given a postings list, where each node in the linked list has 2 pointers, one pointing to the next node and other pointing to a random node in the list. Duplicate this list.

## Solution
- Duplicate each node and carefully link the duplicate node t the next node in the list

    ```ruby
    def duplicate_list(head)
        curr = head

        while curr != nil
            duplicate = Node.new(curr.data)
            duplicate.next = curr.next
            curr.next = duplicate
            curr = duplicate.next
        end
    end
    ```
- Now, for each node update the jump pointer appropriately, using the the fact that the jump pointer of a node in the new list must point to the jump_ptr.next of the original list (since the duplicate is the next node for every node in original list)

    ```ruby
    def update_jump_ptr(head)
        curr = head

        while curr != nil
            curr.next.jump = curr.jump.next if curr.jump != nil
            curr = curr.next.next if curr.next != nil
        end
    end
    ```

- Separate the duplicate nodes from the original list into its own list and return its head

    ```ruby
    def update_next_ptr(head)
        prev = head
        new_head = prev.next
        curr = prev.next

        while curr != nil
            prev.next = curr.next
            curr.next = curr.next.next if curr.next != nil
            prev = prev.next
            curr = curr.next
        end

        new_head
    end
    ```

## Complexity
- Time complexity: O(n) - since we are traversing the list constant (3) times.
- Space complexity: We did not use any additional storage to keep track of the jump pointers.


