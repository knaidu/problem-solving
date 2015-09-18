# Generate binary trees
Given number of nodes, generate all possible binary trees

## Solution
- Split it up into left and right tree nodes
- Start with 0 left subtree nodes and n-1 right subtree nodes (1 left for root)
- Then for each left and right subtree combination, create a root node and add them
- Repeat this for all values of left subtree nodes from 0 to n-1

## Code
```ruby
# Returns a list of binary trees (root nodes)
def generate_binary_trees(n)
    result = []
    
    # Base case, return null node
    return [nil] if n == 0 
    
    i = 0
    while i < n-1
        num_left_nodes = i
        num_right_nodes = n-i-1 # 1 left for root
        left_subtrees = generate_binary_trees(num_left_nodes)
        right_subtrees = generate_binary_trees(num_right_nodes)
        
        left_subtrees.each do |left|
            right_subtrees.each do |right|
                # Create tree with root and left + right tree combinations
                result << BinaryTreeNode.new(0, left, right)
            end
        end
        
        result
    end
end
```