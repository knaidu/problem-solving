# Tree diameter
Given the root node to a tree, find the diameter. Diameter is defined as the longest path between any two nodes in the tree. It may or may not have to pass through the root of the tree.

## Solution
- There are 2 cases, the longest path may or may not pass through the root node
- In the case when it passes through the root node,
    - The new longest path is the sum of top 2 heights of the child nodes
- In the case when it does not pass through the root node
    - The new longest path is the max diameter among all its child nodes
    
## Code
```ruby
def tree_diameter(node)
    
end

# Returns max height and max diameter
def longest_path(node)
    return {0,0}, 0 if node.nil
    
    
end
```