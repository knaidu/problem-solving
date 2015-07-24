# Compute Successor
You have a binary tree where each node has parent pointers, find the successor for a given node.

## Solution
- If right subtree exists, successor is the left most node in the right subtree
- If not, successor is the parent node in the ancestor chain for which the current node belongs in the left subtree.
- Else there is no successor to the node probided

## Code
```ruby
def find_successor(root, node)
    return nil if root.nil? || node.nil?

    # Case 1: Successor is the left most node in the right subtree
    curr = node.right
    while curr
        if curr.left.nil?
            return curr
        else
            curr = curr.left
        end
    end

    # Case 2: Didn't find the node in the right subtree
    curr = node
    while !curr.parent.nil?
        if node = node.parent.left
            return node.parent
        else
            node = node.parent
        end
    end

    # If successor was not yet found, then we dont have one
    return nil

end
```

## Complexity
- Time: O(h) since we're traversing along the height in both cases
- Space: constant
