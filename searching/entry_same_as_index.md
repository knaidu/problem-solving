# Entry same as index
Design an algorithm that takes an array of sorted integers and returns an index i such that the
element at index i equals i.

## Example
```
Input: -2,0,2,3,6,7,9
Output: 2 or 3
```

## Solution
- Trick here is to reduce the problem into a binary search problem

## Code
```ruby
def search(arr)
    return nil if arr.nil?

    low = 0
    high = 0

    while low < high
        mid = ( low + high ) / 2
        if arr[mid] == mid
            return mid
        elsif arr[mid] < mid
            low = mid + 1
        else
            high = mid -1
        end
    end

    return NOT_FOUND
end
```
