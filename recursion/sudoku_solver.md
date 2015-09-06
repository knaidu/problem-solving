# Sudoku solver
Given a partially filled out sudoku board, solve it.

![Partially filled sudoku board](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/500px-Sudoku-by-L2G-20050714.svg.png)

## Solution
- Use recursion to solve the board
- Iterate over all the cells in the board, skip over any non-empty cells
- For an empty cell, check if a value from 1..9 can be inserted
- If it can be inserted then insert the value and recurse onto the next cell
- If not try the next possible number
- Once the board is completely filled stop recursion and return the board

## Code
```ruby
def sudoku(board)
    sudoku_solver(0, 0, board)
end

def sudoku_solver(row, col, board)

    # Reached last col, increment row and reset col
    if col == board.size
        col = 0
        row += 1
    end
        
    # Reached last row, last col, finished solving
    if row == board.size
        return board, true
    end
    
    if board[row][col] != 0
        col += 1
        return sudoku_solver(row, col, board)
    end
    
    # Test all values from 1..9
    for i in 1...9 do
        if valid?(i, row, col, board)
            board[row][col] = i
            col += 1
            board, status = sudoku_solver(row, col, board)
            if status == true
                return true
            end
        end
    end
    
    # None of the values above were valid, backtrack..
    return false
end

def valid?(value, row, col, board)
    # check only the current row, col and box if its valid
    # since that was the only cell that can potentially have an invalid value
end
```
## Complexity
Its NP complete when generalized to n x n grids