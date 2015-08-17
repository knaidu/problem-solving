# Unique elements
Design an efficient algorithm to remove duplicates from an array of integers.

## Solution
- Sort the array in O(n logn)
- Then eliminate duplicates since they would be adjacent elements

## Code
```ruby
def eliminate_duplicates(arr)
    arr = arr.sort
    i = 0
    j = 1
    while j < n
        if arr[j] != arr[j-1]
            arr[i] = arr[j-1]
            i += 1
        end
        j += 1
    end

    arr.truncate(0, i) # trim upto i, rest of the elements are duplicates.
end
```

## Complexity
- Time: O(n logn) to sort the array, O(n) to eliminate duplicates from sorted array
- Space: constance, since its in-place.
