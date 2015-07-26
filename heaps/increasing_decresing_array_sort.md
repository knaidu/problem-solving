# Increasing decresing array sort

Given an array whose elements are in increasing-decreasing order, sort them in the most
effecient manner.

## Example
```
Input: 1, 5, 10, 15, 13, 11, 12, 14, 20, 18, 16, 17, 19, 30
       ----------><------><----------><------><-----------
```

## Solution
- Split the array into a set of sorted increasing arrays
- Then use merge them using a min heap

## Code
```ruby
def sort_increasing_decreasing(arr)
    i = 0
    j = 0
    result = [[]]
    increasing = true
    while i < arr.size
        if arr[i] < arr[i+1] && increasing
            result[j].push(arr[i])
            i += 1
        elsif arr[i] > arr[i+1] && !increasing
            result[j].unshift(arr[i])
            i += 1
        end

        j += 1
        increasing = increasing ? false : true
    end

    sorted_result = merge_sorted_arrays(result)
end
```

## Complexity
- Time
    - O(n) to split the array into increasing sub-arrays,
    - O(n * log n) to merge sorted arrays using min heap
- Space
    - O(n) extra space to hold the sorted sub-arrays
    - We could just do it using pointers to prevent using extra space

