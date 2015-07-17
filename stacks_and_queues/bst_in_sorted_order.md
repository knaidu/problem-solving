# BST in sorted order
Given a BST, print it in sorted order without using recursion

## Solution
- Simulate recursion by explicitly using a stack

## Code
```ruby
def print_bst_in_sorted_order(root)
    return nil unless root

    stack = []
    curr = root

    while !stack.empty? || curr
        if curr # Go left
            stack.push(curr)
            curr = curr.left
        else # Go up
            curr = stack.pop
            result << curr.data
            curr = curr.right
        end
    end
end
```

## Complexity
- Time: O(n) to visit all the nodes in the tree
- Space: O(h) where h is the height of the tree and the stack we've allocated will contain a max of
  h nodes at any given point.
