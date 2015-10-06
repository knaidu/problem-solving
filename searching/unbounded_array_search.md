# Unbounded array search
Given an unbounded array that is sorted, how will you search it for a given element

## Solution
- Simultaneously search for the end of the array and the element given using the binary search technique, doubling the size in each iteration
- If we go beyond the end of the array we'll get an out of bound exception
- Then we can search between previous point and the current out of bound 

## Code
```ruby
def search(arr, key)
    return nil if arr.nil?
    
    i = 0
    prev_i = i
    while true
        begin 
            if arr[i] == key
                return i
            elsif arr[i] < key
                prev_i = i
                i = i * 2
            else
                break
            end
        rescue OutOfBoundException => e
            break
        end
    end
    
    # Now the element is between prev_i and i, do a binary search
    low = prev_i
    high = i
    
    while low <= high
        mid = (low + high) / 2
        begin
            if arr[mid] == key
                return mid
            elsif arr[mid] < key
                low = mid + 1
            else
                high = mid - 1
            end
        rescue OutOfBoundException => e
            high = mid - 1
        end
    end
end
```

## Time complexity
- O(log n) since we first do a search for the end of the array, where we double the text index i in each iteration 
- O(log n) for binary searching once we have found the range in which we have to search.
- Overall O(log n)