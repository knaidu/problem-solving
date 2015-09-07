# K largest elements in a BST
Given k and a bst, find k largest elements

## Solution
- Do a reverse inorder walk on the tree, to start from the right-most node first
- Use a queue to store the elements, as soon as we find k elements stop the walk

## Code
```ruby
def k_largest_elements(root, k)
    return nil if k == 0 || root.nil?
    
    queue = []
    reverse_in_order(k, node, queue)
end

def reverse_in_order(k, node, queue)
    if queue.size < k
        # Recurse on right node first
        queue = reverse_in_order(k, node.right, queue) 
        
        # Ensure queue doesn't have k elements already
        if queue.size < k
        
            # Push the current value
            queue.push(node.value) 
            
            # Then recurse on the left node 
            queue = reverse_in_order(k, node.left, queue) 
        end
    end
    
    return queue
end
```

## Comeplexity
- Time: O(n) for traversing all the nodes, then O(k) for elements in the queue
