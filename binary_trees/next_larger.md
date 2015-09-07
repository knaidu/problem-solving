# Next larger
Given a BST and a value, find the first key that is larger than given value.

## Solution
- Do a BST traverse, and keep track of the larger elements along the way
- BST property ensures we always update the next_larger element as we traverse down to the given value

## Code
```ruby
def next_larger(node, value)
    return nil if node.nil?
    
    nl = 0
    
    while node do
        if node.value > key
            nl = node.value
            node = node.left
        else
            node = node.right
        end
    end
    
    return nl
end
```

## Complexity
- Time: Proportional to the height of the tree, O(log n)