# Longest path length
Given a DAG, where a node x appears before y indicating that x < y (in terms of height of players).
Find the maximum number of players that can be organized according to height given this DAG.

## Solution
- Find the minimum spanning tree for this DAG using DFS
- Save the vertex ordering discovered during DFS
- Now apply BFS using this vertex ordering, calculate the maximum distance from start node
  at each step and update the vertices at each step accordingly.

## Code
```ruby
class GraphVertex
    attr_accesor :label, :distance, :neighbors
end

# Input: g is an array of graph nodes
# Output: vertex_order, an array of graph nodes in topological order
def topological_order(g)
    return nil if g.nil?

    visited = {}
    vertext_order = []

    g.each do |v|
        if !visited.include?(v)
            vertex_order = DFS(v, vertex_order, visited)
        end
    end

    vertex_order
end

def DFS(start_node, vertex_order, visited)
    return if visited.include?(start_node)

    visited[start_node] = true
    start_node.neighbors.each do |v|
        DFS(v)
    end

    vertex_order.push(start_node)
end

def longest_path_length(g)
    vertex_order = topological_order(g)

    max_distance_so_far = 0
    visited = {}

    vertex_order.each do |v|
        next if visited[v]
        max_distance_so_far = [max_distance_so_far, v.distance].max
        v.neighbors.each do |u|
            u.distance = [max_distance_so_far, u.distance]
            visited[u] = true
        end
    end

    max_distance_so_far
end
```

## Complexity
Time: O(E+V) for dfs and then again for BFS
Space: O(E) for storing topological order

