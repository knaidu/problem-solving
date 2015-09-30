# Trapping water
Given an array of non-negative integer specifying the height of each unit wide rectangle, design an algorithm for computing the capacity of the container

## Example
```
|   |
|=|=|=|
|||=|||
-------
Where = is the water filled up and | is a unit height rectangle
```

## Solution
- Observe that the rectangel fills up around the max, therefor compute the capacity on the left and right side separately
- For the left side go from left to max, keep track of max_so far, capacity = diff(max-current_entry)
- For the right side go from right to max, keep track of max_so far, capacity = diff(max-current_entry)

## Code
```ruby
def container_capacity(arr)
    max, max_index = max_element(arr)
    
    # Compute capacity for left side
    i = 0
    max_so_far = 0
    capacity = 0
    while i <= max_index
        if a[i] > max_so_far
            max_so_far = a[i]
        else
            capacity += max_so_far - a[i]
        end
    end
    
    # Compute capacity for right side
    i = arr.size - 1
    max_so_far = 0
    while i >= max_index
        if a[i] > max_so_far
            max_so_far = a[i]
        else
            capacity += max_so_far - a[i]
        end
    end
    
    return capacity
end
```

## Time complexity
- O(n) to find max
- O(n) to find left and right capacity
- Overall O(n)