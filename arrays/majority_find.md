# Majority find
Given an array of elements find the element that occurs more than 50% of the time.

## Solution
- Use moore's voting algorithm
- For every element pair that is different eliminate it
- If any element remains then that's the majority element candidate
- Verify if the candidate is indeed the majority element

## Code
```ruby
def majority_find(arr)
    return if arr.nil?
    
    majority_element = arr[0]
    count = 1
    i = 1
    
    while i < arr.size
        if a[i] == majority_element
            count += 1
        else 
            count -= 1
        end
        
        if count == 0
            majority_element = a[i]
            count = 1
        end
        
        i += 1
    end
end
```

## Time complexity
O(n), additional O(n) for verification