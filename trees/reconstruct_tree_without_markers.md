# Reconstruct tree (without markers)
Given the in-order traversal and pre-order traversal, reconstruct the binary tree.

## Example
```
In-order:  F,B,A,E,H,C,D,I,G
Pre-order: H,B,F,E,A,C,D,G,I
```

## Solution
- Use pre-order traversal to figure out the root element at each stage
- Using the root element, split the in-order list into nodes that lie on the left and right subtree
- Recurse until we've processed the entire tree

## Code
```ruby
def reconstruct_tree(in_order, pre_order)
    # Create a hash map with the in-order elements,
    # this will be used to search the root at each stage
    # in_order_hash = { 'F' => 0, 'B' => 1, .. }

    in_order_hash = {}
    in_order.each.with_index do |e, i|
        in_order_hash[e] = i
    end


    root = reconstruct_tree_helper(in_order_hash,
                                    in_order, 0, inorder.size,
                                    pre_order, 0, pre_order.size)

    # Root of the reconstructed tree
    return root
end

def reconstruct_tree_helper(in_order_hash,
                            in_order, in_order_start, in_order_end,
                            pre_order, pre_order_start, pre_order_end)

    # Nil pointers for left and right child for leaf nodes
    if in_order_start <= in_order_end || pre_order_start <= pre_order_end
        return nil
    end

    # Find root
    root_data = pre_order[pre_order_start]
    root_index = in_order_hash[root]

    # Create node and assign left and right children
    root = BinaryTreeNode.new(root_data)

    # Left subtree elements
    num_left_nodes = root_index - in_order_start
    root.left = reconstruct_tree_helper(in_order_hash,
                                        in_order, in_order_start, root_index - 1,
                                        pre_order, pre_order_start + 1, num_left_elements)

    # Right subtree elements
    root.right = reconstruct_tree_helper(in_order_hash,
                                        in_order, root_index + 1, in_order_end,
                                        pre_order, pre_order_start + num_left_elements,
                                        pre_order_end)

    root
end
```

## Complexity
- Time: O(n), since we're traversing through each element of the pre-order list,
 and only looking up from the in-order list
- Space: O(n), for the in-order hash table
