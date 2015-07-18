# BST Level order
Given a BST, print it in level order.

## Solution
- Use a queue and insert left followed by right child into the queue
- Pop an element print it
- Insert a special node indicating end of level

## Code
```ruby
def level_order(root)
    return nil if root.nil?

    q = []
    q.push(root)

    while !q.empty?
        node = e.pop
        if node.data = -1 # End of level
            puts ''
            next
        end

        puts e.data
        q.insert(node.left)
        q.insert(node.right)
    end
end
```

## Complexity
- O(n) for visiting each node once
