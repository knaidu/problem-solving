# First occurrence of k
Design an algorithm that takes in a sorted array and a key that returns the first occurrence of
the key k.

## Example
```
Array: 1,2,3,4,4,4,5,6,7,8
Key: 4
First occurrence: 3
```

## Solution
- Use binary search, only modification being - don't stop once we find the element
- Let the algorighm gravitate towards the first occurrence of the key

## Code
```ruby
def first_occurrence(arr, k)
    return nil if arr.nil?
    return nil if k > arr.size || k < 0

    low = 0
    high = arr.size
    result = nil

    while low < high
        mid = (low + high) / 2
        if arr[mid] < k
            low = mid + 1
        else // arr[mid] <= k
            high = mid - 1
            result = arr[mid]
        end
    end

    result
end
```

## Complexity
- Time: O(log n) binary search complexity
- Space: Constanct space to keep tract of low, mid and high pointers.
