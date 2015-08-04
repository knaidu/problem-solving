# Longest contained range
Write a program which takes as input an array of integers, and returns the size of a largest subset
of integers in the array having the property that if 2 integers are in the subset then so are all
integers between them.

## Example
```
Input: [3,-2,7,9,1,2,0,-1,5,8]
Output: [-2,-1,0,1,2] with length 6
```

## Solution
- Process the elements into a hash
- Pick each element from the array and expand in both directions until we cannot find it in the
  hash table
- As these elements are found in the has table remove them
- Keep track of max size of subarray seen so far

## Code
```ruby
def longest_contained_range(arr)
    # Insert into hash
    hash = {}
    while arr.each do |e|
        hash[e] = 1
    end

    # Check each element from array
    max = 0
    while arr.each do |e|
        # Element does not exist, or is already part of the longest range
        next unless hash[e]

        break if hash.empty?

        # If element exists in hash
        element = e
        size = 1

        # Expand higher
        while hash[element]
            hash.remove(element)
            element += 1
            size += 1
            max = max(size, max)
        end

        # Expand lower
        element = e - 1
        while hash[element]
            hash.remove(element)
            element -= 1
            size += 1
            max = max(max, size)
        end
    end

    max
end
```

## Complexity
- Time: O(n) for processing the hash, then O(n) for finding the range, total O(n)
- Space: O(n) for storing the elements in hash.
