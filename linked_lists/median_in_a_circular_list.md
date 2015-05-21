# Median in a circular list
Given a circular linked list find the median node

## Solution
- Use the fast ptr slow ptr approach, when the fast ptr reaches the head of the list, then the slow ptr is at the median of the list
    ```ruby
    def find_median
        return @head if @head.next == @head
        return @head if @head.next.next == @head

        fast = @head.next
        slow = @head

        while fast != @head && fast.next != @head
          fast = fast.next.next
          slow = slow.next
        end

        return slow
    end
    ```

## Time complexity
O(n) since we traverse the list only once to find the median
