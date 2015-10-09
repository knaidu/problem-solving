# N-queens problem
Given a chess board with n rows and columns, determine all possible combinations of queen
placements where all the n queens are in non-attacking positions

## Example
```
Input: 4
Output: [[1,3,0,2], [2,0,3,1]]
```

## Solution
- Place the queen in each possible row position and check if there is a conflict
- If there is a conflict
    - then move the queen to next position and repeat
- If there is no conflict
    - keep the queen in that position and recurse to the next row

## Code
```
def n_queens(n)
    placement = []
    result = [] # array of valid placements
    starting_row = 0
    solve_n_queens(n, starting_row, placement)
end

def solve_n_queens(n, row, placement)
    if row == n
        result << placement
    else
        for i in 0..n do
            placement.push(i)
            if valid_placement(placement)
                placement,result = solve_n_queens(n, row+1, placement)
            end
            placement.pop
        end
    end

    placement, result
end

def valid_placement(placement)
    latest_placement = placement.pop
    placement.each.with_index do |p, i|
        diff = Math.abs(p-latest_placement)
        if diff == 0 || diff == i
            return false # Column or diagonal attack
        end
    end

    return true
end
```

## Time complexity
- n! / c^n in other words super exponential
