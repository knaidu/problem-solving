# Traverse 2d array
Given a boolean matrix, where a cell that's false denotes an obstacle, calculate the number of ways we can reach the bottom right cell n-1,m-1 starting at top left 0,0.

## Solution
- In classic DP fashion, use a matrix to keep of the number of ways to reach previous step
- In this case to calculate the number of ways to reach cell n,m, just add the number of ways to reach n-1,m and n,m-1 cell.
- Ensure the first row and first col are pre-populated with num ways as 1

## Code
```ruby
def num_ways(matrix)
    num_ways = [[0] * m] * n
    
    for i in 0..m do
        for j in 0..n do
            if matrix[i][j] == true # No obstacle
                num_ways[i][j] = (i == 0 ? 0 : num_ways[i-1][j]) + (j == 0 ? 0 : num_ways[i-1][j] )
            end
        end
    end
    
    return num_ways[m-1][n-1]
end
```

## Complexity 
O(n*m) due to the 2 loops with