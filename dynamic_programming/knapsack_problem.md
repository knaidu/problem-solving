# Knapsack problem
Given a set of object weight and values, and total capacity of the sack, find the most optimal combination of the objects to fill the sack to max possible value

## Solution
- Start with objects less than weight 1
- Iterate to get to the next level, i.e. objects with weight 2 by using the result from 1
- For every capacity from 0 to max capacity, try every cake which is less than current capacity and see if we can get a better value including this cake in the optimal set


## Code
```ruby
def knapsack(objects, capacity)
    max_val_at_capacity = [0] * capacity
    for cap in 0..capacity do
        max_value_for_cap = 0
        objects.each do |object|
            if object.weight <= cap 
                value_with_curr_object = object.value + max_val_at_capacity[cap - object.weight]
                max_value_for_cap = [max_value_for_cap, value_with_curr_object]
            end
        end
        
        max_val_at_capacity[cap] = max_value_for_cap
    end
    
    max_val_at_capacity[capacity]
end
```

## Time complexity
O(n * k) where n is the number of objects and k is the capacity