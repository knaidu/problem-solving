# Element greater than k
Design an algorithm that analyzes a sorted array and returns the first element that is greater
than key k.

## Example
```
Input: 1,2,3,4,4,5,6,7,7,7,7,8; key = 7
Output: 8
```

## Solution
- Do a binary search, modified to find the right most occurrence of k
- Then return the next element to the right if one exists

## Code
```ruby
def greater_than(arr, k)
    return nil if arr.nil?
    return nil if k.nil?

    low = 0
    high = arr.size

    while low < high
        # More effeciently: mid = low + (high - low) / 2
        mid = (low + high) / 2
        if arr[mid] >= k
            low = mid + 1
            result = mid
        else # arr[mid] < k
            high = mid - 1
        end
    end

    if result < arr.size
        return result + 1
    else
        return nil
    end
end
```

## Complexity
