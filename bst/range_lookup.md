# Range lookup
Given x and y co-ordinates find the closest restaurant. Each restaurant is represented by their co-ordinates

## Solution
- Use 2 BST for storage
- One using x co-ordinate and the other with y co-ordinate
- Do a range lookup on both the BST based on x,y co-ordinate we're looking up
- Now intersect the result of bot the range lookups to get the nearest restaurant
- Here we'll address only the range lookup part of the problem
- Using the BST property, check if a current node is within range or not
- Then traverse only to the left, right or both if the value lies within range

## Code
```ruby
def range_lookup_helper(bst_root, interval)
    result = []
    range_lookup(bst_root, interval, result)
end

def range_lookup(node, interval, result)
    return nil if bst.nil?
    
    # Node is within range, check both children
    if interval.start <= node.value && interval.end >= node.value
        result = range_lookup(node.left, interval, result)
        result << node.value
        result = range_lookup(node.right, interval, result)
        
    # Node is outside the range
    elsif interval.end < node.value
        result = range_lookup(node.left, interval, result)
    else
        result = range_lookup(node.right, interval, result)
    end
    
    return result
end
```

## Complexity
- Time: O(n) since we are potentially visiting all the nodes along the tree.