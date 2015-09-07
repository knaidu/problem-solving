# Test BST
Test if the given tree satisfies the binary search tree property

## Solution 
- For each node test if both left and right child satisfies BST property, 
- Then test the current node and return the status (true/ false)

## Code
```ruby
def bst_checker(node)
    return true unless node
    
    if bst_checker(node.left) && bst_checker(node.right)
        # Test BST property
        return node.left.vale <= node.value && node.value <= node.right.value
    else 
        # Either left or right is not a BST
        return false
    end
end
```

## Complexity
- Time: O(n), where n is the number of nodes