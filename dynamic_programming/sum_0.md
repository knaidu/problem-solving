# Sum 0
Given an array, find the longest sub-array that sums up to 0.

## Solution
- It would be tempting to do recursion, and find all sub-arrays starting at each index (similar to the longest palindrome problem) and then find the longest - that's a O(n^2) algorithm
- Better algo is to track cumulative sum, if the sum has been seen before then we know that elements between current index and prev sum index adds up to 0 sum.
- Repeat this until we reach the end of the array and track the longest sub-array seen so far.

## Code
```ruby
def zero_sub_array(a)
    return if a.nil?
    
    sum = 0
    max_len = 0
    hash = {}
    
    a.each.with_index do |e, i|
        sum += e
        
        if arr[i] == 0 && max_len == 0
            max_len = 1
        end
        
        # Sum was previously seen before
        if hash[sum]
            prev_index = hash[sum]
            max_len = [max_len, i - prev_index].max
        else
            hash[sum] = i
        end
        
        return max_len
    end
end
```

## Complexity
O(n)
