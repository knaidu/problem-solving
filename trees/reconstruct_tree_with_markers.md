# Reconstruct tree (with markers)
You are given pre-order traversal with a slight modification. It includes null pointers when a
particular node has nil left/right child. Reconstruct the binary tree with this information.

## Solution


## Code
```ruby
def reconstruct_tree(pre_order)
    root, index = reconstruct_tree_helper(pre_order, -1)

    root
end

# Explicitly return index to simulate pass by reference
def reconstruct_tree_helper(pre_order, index)
    index += 1

    # Error input
    raise StandardError.new('Invalid input') if index >= pre_order.size

    # Handle nil left/right child
    return nil, index if pre_order[index].nil?

    # Handle non-nil children
    node = BinaryTreeNode.new(pre_order[index])
    node.left, index = reconstruct_tree(pre_order, index)
    node.right, index = reconstruct_tree(pre_order, index)

    node, index
end
```

## Complexity
- Time: O(n) to traverse the entire pre-order list
- Space: O(h), since we are recursing along the height of the tree and storing temp index variables.

