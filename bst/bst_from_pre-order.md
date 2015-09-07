# BST construction from pre-order traversal
Given the pre-order traversal construct the BST

## Solution
- In the pre-order traversal the first element is the root, followed by a sequence of left subtree nodes and right subtree nodes
- Identify that the left subtree nodes are all those values that are less than the current root (bst property)
- Similarly, after x nodes (found in prev step) all values belong to the right node
- Instead of searching through the array of values to find this transition point, just use lower and upper bound values and recurse, ignoring values outside the range specified for the current recursive iteration

## Solution
```ruby
def bst_builder(array)
    return nil if array.nil?
    
    # Set max limits to include all elements to begin recursion
    lower_bound = Integer.min
    upper_bound = Integer.max
    root_index = 0 # Starting with the first value in array (root of the tree)
    bst_builder_helper(array, root_index, lower_bound, upper_bound)
end

def bst_builder_helper(array, root_index, lower_bound, upper_bound)

    # Return nil if element is outside current iteration range
    if array[root_index] < lower_bound || array[root_index] > upper_bound
        return nil
    end
    
    node = BinaryTreeNode.new(array[root_index])
    
    node.left = bst_builder_helper(array, root_index + 1, lower_bound, node.value)
    node.right = bst_builder_helper(array, root_index + 1, node.value, upper_bound)
end
```