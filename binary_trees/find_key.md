# Find key in a BST
Given a number, find if its present in the BST.

## Solution
- Use recursion, go to the left or right subtree based on BST property

## Code
```ruby
def find_key(node, key)
    return false if node.nil?
    
    if node.value == key
        return node
    elsif node.value > key
        return find_key(node.left, key)
    else 
        return find_key(node.right, key)
    end
end
```

## Complexity
- Time: It takes O(log n) to find a key in a BST, its proportional to the height of the tree (logn). Same as binary search in an array. 