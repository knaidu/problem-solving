# Compute kth node in inorder traversal
Write a program that effeciently computes the kth node appearing in an inorder traversal.
Assume that each node stores the number of nodes in the subtree rooted at that node.

## Solution
- By pass the left or right subtree depending on the number of nodes in that subtree
- Keep track of k, when bypassing left subtree, subtract the left_num_nodes + root from k.

## Code
```ruby
def kth_node(root, k)
    if k = root.left.count + 1
        return root
    elsif k > root.left.count + 1
        # Bypass the left sub-tree
        kth_node(root.right, k - root.left.count -1)
    else
        # Bypass the right subtree
        kth_node(root.left, k)
    end
end
```

## Complexity
- Time: O(h) since we're traversing only along the height of the tree and not visiting all the nodes
- Space: O(h), same reasoning.
