# Max subsum in a cicular array
Given an array find the max subsum assuming the array is circular, that is the last element is adjacent to the first element.

## Solution
- Trick: Total sum - Min subsum yields max subsum when array wraps around
- Compute the max subsum without wrap around
- Overall max is max with and without wrap around

## Code
```ruby
def max_subsum_circular(arr)
    sum = 0
    arr.each do |e|
        sum += e
    end
    
    max_s = max_subsum(arr)
    min_s = min_subsum(arr)
    [max_s, sum - min_s].max
end

def max_subsum(arr)
    max_so_far = 0
    sum = 0
    arr.each do |e|
        sum += e
        if sum > max_so_far
            max_so_far = sum
        end
    end
    
    max_so_far
end

def min_subsum(arr)
    min_so_far = 999
    sum = 0
    arr.each do |e|
        sum += e
        if sum < min_so_far
            min_so_far = sum
        end
    end
    
    min_so_far
end
```

## Time complexity 
O(n)