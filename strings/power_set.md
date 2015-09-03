# Power set
Given a set of numbers, generate its powerset

## Example
```
Input: [1,2,3]
Output: [1], [2], [3], [1,2], [1,3], [2,3], [1,2,3]
```

## Solution
- For an array of size n there are 2^n possibilities
- Generate all numbers from 0..2^n, for a set bit include the corresponding set member in the
  result, else skip it.

## Code
```ruby
def power_set(set)
    return nil unless set

    possibilities = 2^set.size
    for i in 0..posibilities do
        result = []
        for j in 0..set.size do
            # Check if bit j is set in i
            if i >> j & 1 == 1
                result << set[j]
            end
        end
        result_set << result
    end

    result_set
end
```

## Time Complexity
- We check each element in the set 2^n times and there are n elements in the set, therefore O(n* 2^n)

