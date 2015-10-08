# Exterior of a tree
Given a binary tree, compute the exterior of the tree. Left view + right view + bottom view.

## Solution
- Trick is to handle the left and right subtree separately
- Calculate the left child at each stage unless left child is not present
- Then compute the leaf nodes
- Repeat the same with the right subtree, mirroring left to right

## Code
```ruby
def exterior(root)
    return nil if root.nil?

    list = []

    # Append root (to prevent repetition)
    list << root

    # Left subtree exterior
    left_exterior(root.left, list, true)

    # Right subtree exterior
    right_exterior(root.right, list, true)

    list
end

def is_leaf?(node)
    node.left.nil? && node.right.nil?
end

def left_exterior(node, list, is_boundary)
    return nil if node.nil?

    # Insert node if its a boundary node as indicated by parent
    # or if its a leaf node
    if is_leaf? || is_boundary
        list << node
        return
    end

    # Traverse to the next node, preserving the boundary property
    if node.left.exists?
        left_exterior(node.left, list, is_boundary)
    elsif node.right.exists?
        is_boundary = is_boundary && node.left.nil?
        left_exterior(node.right, list, is_boundary)
    end
end

def right_exterior(node, list, is_boundary)
    return nil if node.nil?

    # Insert node if its a boundary node as indicated by parent
    # or if its a leaf node
    if is_leaf? || is_boundary
        list << node
        return
    end

    # Traverse to the next node
    if node.left.exists?
        is_boundary = is_boundary && node.right.nil?
        right_exterior(node.left, list, is_boundary)
    elsif node.right.exists?
        right_exterior(node.right, list, is_boundary)
    end
end
```
