# Compute right sibling tree
Given a complete binary tree, assume each node has a sibbling pointer that points to the node
to its right in the graphical representation of the tree. Compute the sibbling node for
every node in the tree.

## Solution
- Key concept here is: update the sibling node for the level below and then
  traverse in level order

## Code
```ruby
def update_sibling(root)
    while root
        update_sibling_helper(root)
        root = root.left
    end
end

def update_sibling_helper(root)
    while root && root.left
        # Update sibling ptr for left and right children
        root.left.sibling = root.right if root.left
        root.right.sibling = root.sibling.left if root.sibling

        root = root.sibling
    end
end
```

## Complexity
- Time: O(n) since we are visiting each node only once
- O(1): constant space

