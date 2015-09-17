# Max subsum
Given an array of positive and negative integers, find the max subsum along with indices.

## Solution
- Max subsum ending at j, is sum of all elements upto j minus min-sum of all elements upto j
 (to account for negative numbers whose sum must be subtracted)

## Code
```ruby
def max_subsum(arr)
    return nil unless arr

    sum = 0
    max_sum = 0
    min_sum = 0
    min_index = 0
    max_start = 0
    max_end = 0

    arr.each.with_index do |e, i|
        sum += e
        if sum < min_sum
            min_sum = sum
            min_index = i
        end

        if sum - min_sum > max_sum
            max_sum = sum - min_sum
            max_start = min_index + 1
            max_end = i + 1
        end
    end
end
```

## Complexity
- Time: O(n) since we do only a single pass over the array
- Space: constant, since we use max of 5 variables to keep track of rolling sum
