# Test BST
Test if the given tree satisfies the binary search tree property

## Solution 
- Test for each child, both of them satisfy BST then test the current node and return the status (true/ false)

## Code
```
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