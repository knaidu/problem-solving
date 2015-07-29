# Find min and max simultaneously
Design an algorithm to find min and max simultaneously with less than 2n-1 comparisons

## Example
```
Input: 3,2,5,1,2,4
Min: 1, Max: 5
```

## Solution
- Trick is to compare in pairs and reduce the number of comparisons by half and therefore n/2-1 comparisons for min and n/2-1 comparisons for max
- Keep running min_so_far, max_so_far and compare them with the min and max condidate obtained
  by comparing pairs

## Code
```ruby
def min_and_max_simultaneously(arr)
    return nil, nil if arr.nil?

    min_so_far = MAX_INTEGER
    max_so_far = MIN_INTEGER
    min_candidate = 0
    max_candidate = 0

    i = 0
    while i < arr.size - 2
        min_so_far = [ [arr[i], arr[i+1].min], min_so_far ].min
        max_so_far = [ [arr[i], arr[i+1].max], max_so_far ].max

        i += 2
    end

    # Compare with last element if there are odd number of elements in the array
    if arr.size % 2 == 1 
        max_so_far = [arr.last, max_so_far].max
        min_so_far = [arr.last, min_so_far].min
    end

    return min_so_far, max_so_far
end
```

## Complexity
- Time: O(n), single pass over the array, with total of 3n/2 - 1 comparisons
- Space: O(1), constant space
