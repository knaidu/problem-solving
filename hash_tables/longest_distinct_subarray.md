# Longest distinct sub-array
Write a program that takes as input an array and returns the length of a longest subarray
with the property that all its elements are distinct.

## Example
```
Input: f,s,f,e,t,w,e,n,w,e
Output: 5 (s,f,e,t,w)
```

## Solution
- Use a hash table to keep track of the last time an element was seen
- Parse through the array and keep track of the largest distinct array seen so far
- Each time we see an element that was seen before,
    - Update the starting index of the current longest distinct array
    - That is the index to the right of the last time the current element was seen
    - Check if this length is greater than the longest distinct array we've seen so far

## Code
```ruby
# Returns length of the longest distinct array
def longest_distinct_array(array)
    last_seen_hash = {}
    max_length_so_far = 0
    start_index = 0

    while array.each.with_index do |e, i|
        if last_seen = last_seen_hash[e]
            if last_seen >= start_index
                index = last_seen_hash[e] + 1
                length = i - index
                if length > max_length_so_far
                    max_length_so_far = length
                end
                start_index = last_seen + 1
            end
        else
            last_seen_hash[e] = i
        end
    end

    max_length_so_far
end
```

## Complexity
- Time: O(n) since we are traversing the array only once
- Space O(n) maintaining the last seen hash for all distinct elements in the array
