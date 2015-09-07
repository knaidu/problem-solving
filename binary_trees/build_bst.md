# Build BST from sorted array
Given a sorted array, build an optimal bst.

## Solution
- Optimal BST is one that is not skewed, with lowest height possible.
- Use the middle element of the array as the root of the BST and then recurse on the left and right sub-tree

## Code
```ruby
def build_bst(array)
    return nil if array.size == 0
    
    middle_index = array.size/2
    node = BinaryTreeNode.new(array[middle_index])
    node.left = build_bst(array[0...middle_index]) # First half excluding middle element
    node.right = build_bst(array[middle_index..-1]) # Second hald

    return node
end
```

## Time complexity
- We're visiting each element of the array only once, therefore O(n).