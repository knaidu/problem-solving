# Sum the root to leaf path
Given a binary tree where each node's data is in binary format. The root to leaf path represents
a number. Sum up all the numbers represented by the binary tree.

## Solution
- Use in-order traversal technique
- Keep track of partial sum
- Use this trick to construct the full binary number as we move towards leaf
    - num = num * 2 + bit

## Code
```ruby
def sum_root_to_leaf(root)
    partial_sum = 0

    sum_root_to_leaf_helper(root, partial_sum)
end

def root_to_leaf_helper(root, partial_sum)
    return 0 if root.nil?

    # Compute partial sum
    partial_sum = partial_sum * 2 + root.data

    # If we've reached a leaf node
    if root.left.nil? && root.right.nil?
        return partial_sum
    end

    # If we've reached non-leaf node
    return root_to_leaf_helper(root.left, partial_sum) +
        root_to_leaf_helper(root.right, partial_sum)
end
```

## Complexity
- Time: O(n) since we're doing a form in-order traversal
- Space: O(h) since we're traversing along the height of the tree using recursion.
