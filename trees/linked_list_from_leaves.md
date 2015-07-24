# Linked list from leaves
Given a binary tree form a linked list from the leaves of the tree in left to right order.

## Solution
- Traverse the tree in pre-order and insert the leaves into a linked list

## Code
```ruby
def connect_leaves(root)
    list = LinkedList.new
    connect_leaves_helper(root, list)

    list
end

def connect_leaves(node, list)
    return nil if node.nil?

    # If leaf node
    list.append(node) if node.left.nil && node.right.nil?

    # If left node exists, recurse
    connect_leaves_helper(node.left, list) unless node.left.nil?

    # If right node exists, recurse
    connect_leaves_helper(node.left, list) unless node.left.nil?
end
```

## Complexity
- Time: O(n) since we're doing a pre-order traversal
- Space: O(l), where l is the number of leaves
