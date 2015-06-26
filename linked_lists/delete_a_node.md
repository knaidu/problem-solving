# Delete a node
Given a pointer to a node, delete that node preferably in O(1)

## Solution
- If the node is not the last node then we can copy the data from then next node, delete the next node and adjust the pointers
- If the node is the last, then we'll have to traverse the list and find prev to last node and then delete the last node
- Tradeoff: If there are any pointers to the next node, they will become dangling pointers

## Code
```ruby
def delete_node(head, node)
    if node.next != NULL
        node.data = node.next.data
        node.next = node.next.next
    else
        prev = find_prev(head)
        prev.next = NULL
    end
end
```

## Complexity
O(1) when the node to be deleted is not the last node in the list
O(n) if it is the last node
