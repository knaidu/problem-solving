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
    count = 0
    
    arr.each.with_index do |e, i|
        if e == majority_element
            count += 1
        else 
            count -= 1
        end
        
        if count == 0
            majority_element = e
            count = 1
        end
    end
end
```

## Time complexity
O(n)