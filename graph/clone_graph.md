# Clone graph
Given a graph G, clone it and return a graph C.

## Solution
- Use BFS traversal to traverse G
- Use a map to keep track of all nodes that have already been cloned
- If a node does not exist in the clone then add it,
- Else add the edge to the clone

## Code
```ruby
class GraphNode
    label = ''
    edges = []
end

def clone_graph(start_node)
    return nil if start_node.nil?

    # BFS traversal
    q = [start_node]
    cloned_q = GraphNode.new(q.label)
    cloned_nodes = {q => cloned_q}
    cloned_graph
    while !q.empty?
        x = q.pop
        x.edges.each do |v|
            if cloned_nodes[v].nil?
                # Add new node
                cloned_v = GraphNode.new(v.label)
                cloned_nodes[v] = cloned_v
                q.add(v)
            end
            
            cloned_nodes[x].edges.push(cloned_nodes[v])
        end
    end

    cloned_nodes
end
```

## Complexity
- Time: O(E+V), since we are doing a bfs traversal to clone the graph
- Space: O(E), since we are storing nodes to be traversed in the queue
