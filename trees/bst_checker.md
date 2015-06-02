# BST checker
Given a binary tree, check if its a BST.

## Solution
- BST criteria is left child value must be less than root value which must be less than right child vlaue
- Do this recursively for each node in the BST

## Code
```ruby
    def check_bst(node, low=MIN, high=MAX)
        return true if node.nil?

        return false if node.value < low || node.value > high

        check_bst(node.left, MIN, root.value) &&
        check_bst(node.roght, root.value, MAX)
    end
```

## Time complexity
O(n) since we are visiting all the nodes in the tree
