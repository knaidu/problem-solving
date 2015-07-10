# Furthest reach
Write a program that takes an array of integers where A[i] denotes the maximum you can advance
from index i, and returns true if its possible to advance to the last index in the array,
starting at the first index in the array.

## Example
```
can_reach_end([3,3,1,0,2,0,1]) #=> true
can_reach_end([3,2,0,0,2,0,1]) #=> false
```

## Solution
- Key here is to keep track of the furthest reach from every index
- Traverse the array extending the reach from every index and allowing traversal upto the
  furthest reach calculated
- If we reach the end of the array return true, else return false

## Code
```ruby
def can_reach_end(arr)
  furthest_reach = 0
  i = 0

  while (i <= furthest_reach)
    furthest_reach = [furthest_reach, i + arr[i]].max
    i += 1
    return true if furthest_reach > arr.size - 1
  end

  return false
end
```

## Complexity
O(n) time, where n is the number of elements in the given array
