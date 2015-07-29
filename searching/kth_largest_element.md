# Kth largest element
Given an array of distinct integers, find the kth largest element

## Solution
- Use the pivot technique from quick-sort
- Find random integer r between 0..n, and partition it such that the element lies in its final sorted position
- If there are k-1 elements before r then we have found the kth element
- If not then recurse on the left or right depending on where r lies

## Code
```ruby
def kth_largest_element(arr, k)
    start = 0
    end = arr.size

    kth_largest_element_helper(arr, k, start, end)
end

def kth_largest_element_helper(arr, k, start, end)
    r = random_number_generator(start, end)

    # Partition
    low = start
    high = end
    num = arr[r]

    # Move it the end and restore after paritioning
    swap(arr, r, end)

    # Partition the array
    # Elements to the left should be less than pivot
    # and elements to the right should be greater than pivot
    while low < high
        if arr[low] < num
            low += 1
        elsif arr[high] > num
            high -= 1
        else
            swap(arr, low, high)
        end
    end

    # Restore pivot element to its final place
    swap(arr, high, end)

    # Compare and recurse if necessary
    if high == k
        return arr[high]
    elsif high < k
        return kth_largest_element_helper(arr, k, start, high)
    else
        return kth_largest_element_helper(arr, k - high, high, end)
    end
end
```

## Complexity
- Time: O(n) to parititon and recurse util we find k
- Space: O(1) constant space
