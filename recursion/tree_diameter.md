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
def height_and_diameter(node)
    return 0, 0 if node.nil
    
    # Track top 2 heights among all the children
    # This includes the path from current node to those children
    height = [0, 0]
    diameter = 0
    
    node.edges.each do |e|
        h, d = height_and_diameter(e)
        
        # Check if we have found a new max height
        # e.length is the distance from node to e
        if h + e.length > h[0] 
            h[1] = h[0]
            h[0] = h + e.length
        elsif h + e.length > h[1]
            h[1] = h + e.length
        end
        
        # Update diameter to be max among all children
        diameter = max(diameter, d)
    end
    
    # h[0] is the max height found among all children
    # diameter is the max among all children, find the max including a path through current root
    
    return h[0], max(diameter, h[0] + h[1])
end
```

## Complexity
- Time: We're visiting each node only once and bubbling up the max height and diameter at every stage,
  therefore its linear in the order of nodes, O(|V|) where v is number of nodes