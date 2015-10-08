# LCA with close ancestors
Design an algorithm for computing LCA of the two nodes in a binary tree. The algorithm's time
complexity should only depend on the distance between the nodes and not the height of the tree.

## Solution
- Use a tandem approach alternating between the two nodes
- Each time we traverse to the parent node check if it has been visited before using a hash table
- If it has been visited, then that is the LCA

## Code
```ruby
def lca(node1, node2)
    hash = {}
    while node1 && node 2
        if node1
            if hash[node1]
                return node1
            else
                hash[node1] = true
                node1 = node1.parent
            end
        end
        if node2
            if hash[node2]
                return node2
            else
                hash[node2] = true
                node2 = node2.parent
            end
        end
    end

    return not_found
end
```

## Complexity
- Time O(s) where s is the distance between the two nodes
- Space O(s) for the hash table
