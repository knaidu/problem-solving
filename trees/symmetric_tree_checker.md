# Symmetric tree check
Given a binary tree, check if its symmetric.

## Solution
- A tree is symmetric if its same as its mirror image
- Trick here is to compare without creating a mirror image and simulate that in recursion

## Code
```ruby
def is_symmetric_tree(root)
    return true if root.nil?

    check_symmetric(root.left, root.right)
end

def check_symmetric(first, second)
    return true if first.nil? && second.nil?

    if !first.nil? && !second.nil?
        # Compare with mirror image tree, hypothetically
        return first.data == second.data &&
            check_symmetric(first.left, second.right) &&
            check_symmetric(first.right, second.left)
    end

    return false
end
```

## Complexity
- Time: O(n) visiting each node once using recursion
- Space: O(h) max height of the tree
