# Lowest common ancestor in a BST
Given values of 2 nodes that exist in the BST, find their lowest common ancestor.

## Solution
- For every node check where the 2 values lie,
    - If they lie on either side of the current node, then current node is the LCA
    - If both lie on the left or right, then recurse on the left or right subtree

## Code
```ruby
def lca_for_bst(node, value1, value2)
    return nil if node.nil?
    
    if value1 <= node.value && value2 >= node.value
        node
    elsif value1 < node.value && value2 < node.value
        lca_for_bst(node.left)
    else
        lca_for_bst(node.right)
    end
end
```

## Complexity
- O(h) since we're following a BST traversal in this case to find the LCA node.