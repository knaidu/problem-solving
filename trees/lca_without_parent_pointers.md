# LCA without parent pointers
Given the root of a binary tree, and 2 nodes, determine the LCA. Note: The nodes do not have
parent pointers.

## Solution
- Use a recursive solution
- If both nodes are present in the left subtree, recurse towards the left
- If both are present in the right subtree, recurse towards the right
- If one is in the left and other is on the right, then we have found out LCA.
- To prevent revisiting some of the nodes, return the lca and num nodes found in each subtree

## Code
```ruby
def find_lca(root, node1, node2)
    lca, num_nodes = lca_helper(root, node1, node2)

    return lca
end

def lca_helper(root, node1, node2)
    return 0, nil if node1.nil?
    return 0, nil if node2.nil?

    # Test if lca is in the left subtree
    left_lca, left_num = lca_helper(root.left, node1, node2)
    return left_lca if left_num == 2

    # Test if lca is in the right subtree
    right_lca, right_num = lca_helper(root.right, node1, node2)
    return right_lca if right_num == 2

    # When each node is on either side of the current root
    num = left_lca + right_lca

    # When one node is in the parent chain of the other
    num += 1 if root == node1 || root == node2

    # If LCA is found return it, else return nil to continue looking for LCA
    lca = num == 2 ? root : nil

    return num, lca
end
```

## Complexity
- Time: O(n), since we are doing a form of pre-order traversal.
- Space: O(h), since we are storing temporary nodes while recursing along the height of the tree.
