# Search in a sorted matrix
Design an algorithm to search a 2D sorted matrix

## Solution
- Start from top right and move left or bottom depending on the comparison with key

## Code
```ruby
def sorted_matrix_search(arr, key)
    # Start from top right element
    i = 0
    j = arr[0].size

    while arr[i][j] != key || i < arr.size || j > 0
        if arr[i][j] < key
            i += 1
        elsif arr[i][j] > key
            j -= 1
        else
            return i,j
        end
    end

    return -1,-1
end
```
