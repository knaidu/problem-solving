# Array permutations
Given an array, print all its permutations

## Example
```
[1,2,3] => [1,2,3], [1,3,2], [2,1,3], [2,3,1], ...
```

## Solution
- Use a recursive solution, swapping 2 array elements at a time in order
- Be sure to swap back the elements so that we can continue backtracking
  and do not repeat permutations
- Use this tree come up with the recursive solution http://d2dskowxfbo68o.cloudfront.net/wp-content/uploads/NewPermutation.gif

## Code
```ruby
def permute(arr, k)
  i = k
  while i <= k
    swap(arr, i, k)
    permute(arr, k+1)
    swap(arr, i, k)
    i += 1
  end

  if(k == arr.size - 1)
    puts arr.inspect
  end
end

def array_permutations(arr)
  permute(arr, 0)
end
```

## Complexity
Time: O(n * n!)
