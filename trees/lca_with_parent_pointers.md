# LCA with parent pointers
Given a binary tree where each node also stores parent pointer in addition to left and right node. Given 2 nodes, find their LCA.

## Solution
- Essentially bring both the nodes to the same level and then scale up towards the root while looking for the LCA.
- Find the length from each of the nodes to the node to root
- Descend from the deeper node until the level of both nodes is the same
- Now decent towards root while checking for LCA

## Code
```ruby
def find_lca(root, node1, node2)
    height1 = find_height(node1, root)
    height2 = find_height(node2, root)

    if height1 > height2
        lower_node = node2
        higher_node = node1
    else
        lower_node = node1
        higher_node = node2
    end

    # Descent until both nodes are the same height
    diff = Math.abs(height1 - height2)
    while diff > 0
        lower_node = lower_node.parent
        diff -= 1
    end

    while lower_node != higher_node
        lower_node = lower_node.parent
        higher_node = higher_node.parent
    end

    return lower_node
end
```

## Complexity
- Time: O(h), since we're traversing the tree along the height 3 times at max.
