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
    
    median = find_median(arr)
    
    diff_pair_array = []
    arr.each do |e|
        diff_pair_array << {median - e, e}
    end
    
    kth_smallest_index, diff_pair_array = find_kth_smallest(diff_pair_array, k)
    
    get_first_k_elements(diff_pair_array)
end

def get_median(arr)
    find_kth_smallest(arr, arr.size/2) if arr.size %2 == 0 # Even
    find_kth_smallest(arr, arr.size/2+1) # for odd number of elements
end
```

## Time complexity
- O(n) for finding median
- O(n) for creating diff_pair array
- O(n) for finding kth smallest element
- O(n) to extract first k elements closest to k