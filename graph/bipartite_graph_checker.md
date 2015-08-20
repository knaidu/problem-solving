# Bipartite graph checker
Given a graph check if its bipartite, i.e. can it be split into 2 groups of vertices, such that
there is an edge from one side to the other.

## Solution
- Use a simple numbering scheme where the odd vertices go to one side and the even vertices go to
 the other

## Code
```ruby
def bipartite_graph_checker(start_node)
    return false if start_node.nil?

    q = [start_node]
    start_node.d = 0

    while !q.empty?
        node = q.pop

        node.edges.each do |e|
            q.push(e)
            if e.d != node.d
                e.d = node.d + 1
            else
                # Cannot be bipartite
                return false
            end
        end
    end

    return true
end
```

## Complexity
- Time: O(E+V), since we are doing BFS traversal
- Space: O(V), since we are storing all the nodes in the queue for processing
