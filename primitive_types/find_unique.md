# Find unique
Given the array of IDs, which contains many duplicate integers and one unique integer, find the unique integer.

Note: All integers except one appear exactly 2 times.

## Example
```
[1,2,3,4,1,2,3] #=> 4
[1,2,1,2] #=> 0
[1] #=> 1
```

## Solution
- Key concept here is how XOR operator works. When applied to the same integers it returns 0.
- Therefore we can use it to XOR all the numbers, each duplicate pair will 'cancel'  out and the remaining element will be the unique one.

## Code
```ruby
def find_unique(array)
  return array[0] if array.size == 1

  i = 0
  unique_number = array[i]

  while i < array.size - 1
    i += 1
    unique_number = unique_number ^ array[i]
  end

  return unique_number
end
```

## Time complexity
O(n) since we're visiting all elements in the array only once.

