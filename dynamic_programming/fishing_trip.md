# Fishing trip
Given a 2d array filled with numbers indicating fish, plan a trip from 0,0 cell to n-1,m-1 cell maximizing the number of fish picked along the way. 

## Solution
- The key concept here is: for cell x,y pick max(fish(x,y-1), fish(x-1,y))
- Do this in a DP way storing the intermediate values in a matrix until we reach the last n-1,m-1 cell

## Code
```ruby
def fishing_trip(matrix)
    max_fish = [[0]*n]*m
    
    max_fish[0][0] = matrix[0][0]
    for i in 0..m do
        for j in 0..n do
            if matrix[i][j] != -1 # Not an obstacle
                max_fish[i][j] += max((i==0 ? 0 : matrix[i-1][j]), (j==0 ? 0 : matrix[i][j-1]))
            end
        end
    end
    
    return max_fish[m-1][n-1]
end
```

## Time complexity
- O(mn) due to the 2 loops for iterating over the matrix.