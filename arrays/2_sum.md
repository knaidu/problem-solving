# 2 SUM
Given an array, find a pair in the array that would add up to the given sum.

## Example
```
find_pair(array = [1,2,3,4,5], sum = 5) => Pair: 1 and 4
```

## Algorithm
- Traverse the array, for every element check
    - If (sum - element) exits
    - If it does return true, else insert sum - element into a hash

## Code
```ruby
def find_pair(array, sum)
  i = 0
  pair_exists = {}
  while i < array.size
    if pair_exists.include?(array[i])
      return true
    else
      pair_exists[sum - array[i]] = true
    end
    i += 1
  end

  return false
end
```

## Time complexity
O(n) - to process the array into a hash
O(n) - to traverse the array to find sum-x element
O(1) - to lookup sum-x in the hash table
Overall: O(n+n) = O(n)
