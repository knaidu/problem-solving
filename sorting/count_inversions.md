# Count number of inversions 
Given an unsorted array, count the number of inversions.

## Solution
- Use the merge sort algorithm and enhance it with the inversion count
- In the merging step, count inversions
    - if value in a > value in b, then inversions = a.end - a_index  
- Repeat this until the entire array is merged

## Code
```ruby
def count_inversions(arr)
    merge_sort(arr, 0, arr.size)
end

def merge_sort(arr, left, right)
    return 0 if left >= right
    mid = (left + right) / 2
    inversions = 0
    inversions += merge_sort(arr, 0, mid)
    inversions += merge_sort(arr, mid, right)
    inversions += merge(arr, left, mid, right)
    return inversions
end

def merge(arr, first, second, end)
    temp = []
    inversions = 0 
    i = first
    j = second
    
    while i < second && j < end
        if arr[i] <= arr[j]
            temp << arr[i]
            i += 1
        else
            temp << arr[j]
            inversions += second - i
            j += 1
        end
        
    end
    
    i = first
    j = 0
    while i < end
        arr[i] = temp[j]
        i += 1
    end
    
    return inversions
end
```