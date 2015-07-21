# Root-leaf path with specified sum
Write a program which takes as input an integer and a binary tree with integer
weights, and checks if there exists a leaf whose path weight equals the specified sum.

## Solution
- Recursively compute sum as we visit the nodes
- When we find a leaf node check if the sum equals the specified sum

## Code
```ruby
def root_to_leaf_sum_check(root, sum)
    partial_sum = 0
    root_to_leaf_sum_check_helper(root, sum, partial_sum)
end

def root_to_leaf_sum_check_helper(root, specified_sum, partial_sum)
    return false if root.nil?

    # Leaf node
    if root.left.nil? && root.right.nil?
        return partial_sum == specified_sum
    end

    return root_to_leaf_sum_check_helper(root.left, specified_sum, partial_sum) ||
        root_to_leaf_sum_check_helper(root.right, specified_sum, partial_sum)
end
```

## Complexity
- Time: Essentially its pre-order traversal, so O(n)
- Space: O(h) in the order of the height of the tree.
