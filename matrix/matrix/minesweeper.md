# Minesweeper
Given a matrix, number of rows, number of columns and number of mines, populate a minesweeper board, that is ready to play.

## Example
```
1 mine in a 3x3 board

| 1 1 1 |
| 1 * 1 |
| 1 1 1 |

```

## Solution
- Approach 1 is to randomly drop the mines, once all the mines are dropped then calculate count for
  all non-mine cells by examining each cell and counting the number of mines around it.
- Better solution is to drop a mine and immediately increment all the cells around it, repeating
  this until all the mines have been randomly dropped

## Code
```ruby
def populate_mines(matrix, mine_count)
    rows = matrix.size
    cols = matrix[0].size

    while mine_count != 0
        rand_row = random_number_generator(rows) # Rand number between 0..row
        rand_col = random_number_generator(cols) # Rand number between 0..col

        if matrix[rand_row][rand_col] != '*'
            matrix[rand_row][rand_col] = '*'
            mine_count -= 1
            increment_count(rand_row, rand_col)
        end
    end
end

def increment_count(i ,j)
    matrix[i-1][j-1] += 1 if i-1 > 0 && j-1 > 0 && not_mine
    matrix[i-1][j] += 1 if i-1 > 0 && not_mine
    matrix[i-1][j+1] += 1 if i-1 > 0 && j+1 < rows && not_mine
    matrix[i][j+1] +=1 if j+1 < rows && not_mine
    matrix[i+1][j+1] += 1 if i+1 < cols && j+1 < rows && not_mine
    matrix[i+1][j] += 1 if i+1 < cols && not_mine
    matrix[i+1][j-1] += 1 if i+1 < cols && j-1 > 0 && not_mine
    matrix[i][j-1] += 1 if j-1 > 0 && not_mine
end
```

## Complexity
O(n) to drop n mines, constant time to increment all the countsap
