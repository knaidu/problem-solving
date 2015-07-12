# Spiral order
Given a 2D matrix, print it in spiral order.

## Solution
- Print row => col => row_reverse => col_reverse
- Adjust the row_start, row_end, col_start, col_end appropriately at each stage using concrete
  examples

## Code
```ruby
def spiral_order(arr)
  row_start = 0
  col_start = 0
  row_end = arr.size
  col_end = arr.size

  result = []
  while col_start <= col_end
    row = row_start
    col = col_start
    while col < col_end
      result << a[row][col]
      col += 1
    end

    col = col_end - 1
    row = row_start + 1

    while row < row_end
      result << a[row][col]
      row += 1
    end

    row = row_end - 1
    col = col_end - 2
    while col >= col_start
      result << arr[row][col]
      col -= 1
    end

    col = col_start
    row = row_end - 2
    while row > row_start + 1
      result << arr[row][col]
      row -= 1
    end

    row_start += 1
    col_start += 1
    row_end -= 1
    col_end -= 1
  end

end
```

## Time complexity
- O(n) where n is the number of elements in the array
- Or O(m x n), more common representation for 2D arrays,
  where m is the number of rows and n is the number of columns
