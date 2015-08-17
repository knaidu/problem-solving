# BFS traversal
Given a graph, print all the nodes by performing BFS traversal

## Code
```ruby

class GraphNode
    label = ''
    edges = []
end

def bfs_traversal(start_node)
    return nil if start_node.nil?

    q = [start_node]
    while !q.empty?
        // Examine edges of q
        x = q.remove_front
        x.edges.each do |e|
            puts e.label
            q.add_back(e)
        end
    end
end
```

## Time complexity
- Time: O(E+V) where e is the number of edges and V is the number of vertices
- In other words BFS operates in linear time
- Space: O(V) since we are storing the vertices to be parsed in a queue
