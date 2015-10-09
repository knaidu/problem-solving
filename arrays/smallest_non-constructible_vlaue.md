# Smallest non-constructable value
Given an array of integers (representing coins), find the smallest value that cannot be constructed from those integers.

## Solution
- Key observation here is, when the integers are sorted, we can always track the highest constructable value by doing a cumulative sum of the sorted integers
- At any point if the next integer is larger than max_constructible_so_far + 1, then we have found our smallest non-constructable value

## Code
```ruby
def smallest_non_constrictible_value(arr)
    return nil if arr.nil?
    
    arr.sort
    
    max_constructible = 0
    arr.each do |e|
        if e > max_constructible + 1
            break
        end
        
        max_constructible += e
    end
    
    return max_constructible + 1
end
```

## Time complexity
O(n log n) to sort, and O(n) to find the result, overall O(n log n)