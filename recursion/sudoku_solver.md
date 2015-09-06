# Sudoku solver
Given a partially filled out sudoku board, solve it.

## Solution
- Use recursion to solve the board
- Iterate over all the cells in the board, skip over any non-empty cells
- For an empty cell, check if a value from 1..9 can be inserted
- If it can be inserted then insert the value and recurse onto the next cell
- If not try the next possible number
- Once the board is completely filled stop recursion and return the board

## Code
```ruby

```