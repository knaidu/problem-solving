# Postings list jump-order
Given a postings list, where each node has a next pointer and a jump pointer that points to
random node int the list. Find the jump-order, assume each node also has an order field that is
initialized to -1.

## Solution
Jump order is to follow the jump node and then the next node until all nodes have been visited.

## Code
```
def jump_order(head)
    order = 0
    jump_order_helper(head, order)
end

def jump_order_helper(node, order)
    if node
        order += 1
        node.order = order
        jump_order_helper(node.jump, order)
        jump_order_helper(node.next, order)
    end
end

def jump_order_recursive(head)
    order = 0
    stack = []
    stack.push(head)

    while !stack.empty?
        curr = stack.pop
        order += 1
        curr.order = order

        # LIFO, push next then jump
        stack.push(curr.next) unless curr.next.nil?
        stack.push(curr.jump) unless curr.jump.nil?
    end
end
```

## Complexity
- Time: O(n) where n is the number of nodes in the postings list
- Space: O(n) for the stack
