# Rotation point
Write a function for finding the "rotation point". This array is huge so we want to be efficient here.

## Example
```
i/p: [35,42,5,15,27,29]
o/p: 2
```

## Solution
- Use the binary search technique to find the rotation point
- When the left and right pointers are next to each other we have found the rotation point

## Code
```ruby
def find_rotation_point(array)
  left = 0
  right = array.size

  first = array[0]

  while left < right
    mid = (left + right) / 2

    array[mid] > first ? left = mid : right = mid

    return right if left + 1 == right

  end
end
```

## Complexity
- O(log n) since we are using the binary search technique to eliminate half of the array in each iteration
- We're using constant space O(1) for maintaining the left, right and mid indices
