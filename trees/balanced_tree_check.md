# Balanced tree check
Given a binary tree, test if the tree is balanced.

## Solution
- A tree is balanced if difference between left subtree height and right subtree height is
  not more than 1.
- Trick here is to combine height calculation while recursing and checking if the sub-tree
  is balanced.

## Code
```ruby
def balanced?(root)
    return true, -1 if root.nil?

    left_result, left_height = balanced?(root.left)
    return false, -1 if !left_result

    right_result, right_height = balanced?(root.right)
    return false, -1 if !right_result

    height = max(left_height, right_height) + 1
    if Math.abs(left_height - right_height) <= 1
        return true, height
    end

    return false, -1
end

```

## Time complexity
O(n) since were doing a form of post order traversal



