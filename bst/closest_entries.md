# Find closest entries from 3 sorted arrays
Given 3 sorted arrays, find one entry from each of the arrays such that their difference is minimal.

## Example
```
Input:
a = [5,10,15]
b = [3,6,9,12,15]
c = [8,6,14]

Output: [15,15,16]
         a  b  c - elements picked from arrays
```

## Solution
- Load the first element from each array into a data structure X
- Find the min, max and difference
- If the difference is lower that previously found difference then update it with the latest
- Now remove the min element and insert the next element from the respective array, i.e if min came from array a, then add the next element from a.
- Repeat this until we hit the end of any of the arrays
- The data structure best suited to do this is a multi map in C++ or generically a BST, since it can return min, max and can hold duplicate values, or a red black tree (an implementation of BST).

## Code
```ruby
def find_closes_entries(arrays)
    # Each node contains value from an array and the index of that array
    rb_tree = RBTree.new()
    
    # Populate rb_tree node with the first element from each of the arrays
    arrays.each.with_index do |arr, i|
        rb_tree_node = RbTreeNode.new(arr.first, i) # Value and index pair
        rb_tree.add(rb_tree_node)
    end
    
    result = Integer.max
    
    while true do
        # Find the closest entries and update if its better with the current set
        min_node = rb_tree.min 
        max_node = rb_tree.max
        diff = max.value - min.value
        if result > diff
            result = diff
            result_elements = update_current_set_of_values(rb_tree)
        end
        
        # Remove the minimul element
        rb_tree.delete(min_node)
        
        # Remove first element from the array where we found min element
        a = arrays[min_node.index]
        a.remove_front
        break if a.size == 0
        
        # Add the next element from the array in consideration
        next_node = RbTreeNode.new(a.first, min_node.index)
        rb_tree.insert(next_node)
    end
    
    return result_elements
end
```