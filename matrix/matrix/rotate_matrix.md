# Rotate matrix
Given a 2d array, rotate it by 90 degrees

## Example
```
1  2  3  4       13 9  5  1
5  6  7  8    => 14 10 6  2
9  10 11 12      15 11 7  3
13 14 15 16      16  2 8  4
```

## Solution
- Start from the boundaries, 1,4,16,13 in the above example
- Do a four way swap (in clock wise direction)
- Move to the next elements (in clockwise direction)
- Repeat this until all elements have been swapped
- Shrink the matrix to the next inner layer and repeat

## Code
```ruby
def rotate_matrix(arr)
  row_start = 0
  col_start = 0
  row_end = arr.size
  col_end = arr.size

  while row_start < row_end && col_start < col_end
    # Setup the boundary points
    r1 = row_start
    c1 = col_start
    r2 = row_end-1
    c2 = col_start
    r3 = row_end - 1
    c3 = col_end -1
    r4 = row_end - 1
    c4 = col_start

    (0...arr.size).times do
      # Four way swap
      temp = arr[r1][c1]
      arr[r1][c1] = arr[r2][c2]
      arr[r2][c2] = arr[r3][c3]
      arr[r3][c3] = arr[r4][c4]
      arr[r4][c4] = temp
      c1 += 1
      r2 += 1
      c3 -= 1
      r4 -= 1
    end

    # Shrink the boundaries of the matrix
    row_start +=1
    col_start +=1
    row_end -= 1
    col_end -= 1
  end
end
```

## Time complexity
- O(m x n) where m is the number of rows and n is the number of columns in the matrix
