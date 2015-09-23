# Longest increasing sub-sequence
Given an array of integers, find the longest increasing sub-sequence

## Solution
- Start examining the array from left to right, keep track of the longest sequence seen so far
- Once the sequence is no longer increasing restart the count and check if the next sequeunce is longer than the previous one seen
- Repeat this until the end of array
- We'll need additional book-keeping if we want to track the starting and ending indices of the LIS.

## Code
```ruby
def lis(arr)
    return nil if arr.nil
    
    i = 1
    lis_length = 0
    while i < arr.size do
        length = 0
        while arr[i-1] <= arr[i]
            i += 1
            length += 1
            lis_length = max(lis_length, length)
            break if i == arr.size
        end
        i += 1
    end
end
```

## Time complexity
- O(n) since we are looping over all the elements only once