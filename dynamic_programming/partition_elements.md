# Partition elements
Given a set of numbers, partition them into 2 sections, such that the difference is minimal

## Solution
- Create an array T that will hold all possible sums that the given set can generate
- T[x] = true means sum x can be created using the elements provided
- To generate this array, for each element, 
    - check for all values from sum-element down to 0 if its true, if it is then set T[value] to true
- Once the array is generated, check sum/2 (equal split) is true
- If not the continue searching in the range sum/2 .. 0

## Code
```ruby
def partition_problem(elements)
    return nil if elements.nil?
    
    sum = 0
    t = [0] * (elements.size + 1)
    
    elements.each do |e| 
        sum += e
    end
    
    elements.each do |e|
        for j in sum/2-e..0 do
            if t[j]
                t[j+element] = true
            end
        end
    end
    
    i = sum/2
    while i > 0
        if t[i]
            return sum - (2 * i) # minimum difference
        end
    end
    
    return sum
end
```

## Time complexity
O(n * sum)