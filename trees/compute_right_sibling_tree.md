# Compute right sibling tree
Given a complete binary tree, assume each node has a sibling pointer that points to the node
to its right in the graphical representation of the tree. Compute the sibling node for
every node in the tree.

## Solution
- Key concept here is: update the sibling node for the level below and then
  traverse in level order

## Code
```ruby
def update_sibling(root)
    # Process each level, starting at the left most node
    while root

        # No need to traverse last row
        while root && root.left
            # Update sibling ptr for left and right children
            root.left.sibling = root.right if root.left
            root.right.sibling = root.sibling.left if root.sibling

            root = root.sibling
        end
        root = root.left
    end
end
```

## Complexity
- Time: O(n) since we are visiting each node only once
- O(1): constant space

