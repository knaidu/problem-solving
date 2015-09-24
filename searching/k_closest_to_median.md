# Find K closest elements to the median
Given an unordered array, find the k closest elements to the median of the array

## Solution
- First find the median
- Determine the difference between median and each of the elements
- Now we need to pick the k closest or k smallest
- Use the kth smallest element algorithm to get the result

## Code
```ruby
def k_closest_to_median(arr, k)
    return nil if arr.nil? || k == 0
end
```