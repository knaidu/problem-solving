# Increment BigInteger
Given an integer whose digits are represented as an array, increment it and return the result.

## Example
```
increment([1,2,3]) #=> [1,2,4]
increment([9,9,9]) #=> [1,0,0,0]
```

## Solution
- Parse the array from R to L, use the sum and carry technique
- Remember there may be cases where we will have to insert a digit at the leftmost
  location in the array

## Code
```ruby
def increment(arr)
  return nil if arr.nil?

  i = arr.size - 1
  arr[i] += 1

  while i > 0 && arr[i] == 10
    arr[i] = 0
    i -= 1
    arr[i] += 1
  end

  if arr[0] == 10
    arr[0] = 0
    arr = [1].concat(arr)
  end

  arr
end
```

## Complexity
Time: O(n) where n is the number of digits in the big integer
