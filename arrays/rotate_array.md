# Rotate array
Given an array and an integer k, rotate the array k times.

## Example
```
rotate([1,2,3,4,5], 2) #=> [3,4,5,1,2]
rotate([1,2,3,4,5], 4) #=> [5,1,2,3,4]
rotate([1,2,3,4,5], 5) #=> [1,2,3,4,5]
```

## Solution
- To do it in place without using additional space, the trick is in reversing the array appropriately
- Reverse the first part 0..i, reverse the second part i..n, then reverse the entire array

## Code
```ruby
def rotate_array(arr, i)
  i = i%arr.size
  return arr if i == 0

  left = arr[0...i].reverse
  right = arr[i..arr.size].reverse
  arr = left + right

  arr.reverse
end
```

## Complexity
Time: O(n), max of 3 traversals over the array
Space: No additional space used



