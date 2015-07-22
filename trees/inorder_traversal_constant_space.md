# Inorder traversal constant space
Given a binary tree with parent node pointers, implement an inorder traversal using constant space.

## Solution
- Use the parent pointer to nagivate from child to parent and testing which node must be
 processed next

## Code
```ruby
def in_order_traversal(root)
    return if root.nil?

    curr = root
    prev = nil
    next = nil

    while !curr.nil?
        # Came down from parent
        if curr.parent = prev

            # Go left if possible
            if !curr.left.nil?
                next = curr.left

            # Go up to parent
            else
                puts curr.data
                next = curr.parent
            end

        # Came up from child
        elsif curr.left = prev
            puts curr.data
            next = curr.right if !curr.right.nil?

        # Done printing both children
        else
            curr = curr.parent
        end

        prev = curr
        curr = next
    end
end
```
