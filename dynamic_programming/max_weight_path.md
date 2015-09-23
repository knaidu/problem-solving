# Max weight path in a triangle
Given an array of array of integers representing a triangle (like pascals triangle), find the max weight path through it, such that you can traverse only from top to bottom using only adjacent integer values

## Example
```
   1
  2 3
 4 5 6
 
Max path is 1->3->6: 10
```

## Solution
- Use an array to keep track of the max weight moving from previous row to the next row
- For each element in current row, pick the max of the 2 adjacent elements from prev row (prev_row[j-1], prev_row[j])
- Add the max to the current element 
- Repeat this until we reach the last row, after each row is processed swap prev and current row, since we no longer need to keep track for prev row information

## Code
```ruby
def max_weight(arr)
    return nil if arr.nil?
    
    num_rows = arr.size
    prev_row = arr.first
    
    # Evaluate one row at a time
    for i in 1..num_rows do
        curr_row = arr[i]
        curr_row.first += prev_row.first
        
        # Evaluate each element in current row
        for j in 1..curr_row.size do
            curr_row[j] += max(prev_row[j-1], prev_row[j])
        end
        
        curr_row.last += prev_row.last
        
        prev_row = curr_row
    end
    
    # Find max weight in the final cummulative sum row
    max_weight = 0
    curr_row.each do |e|
        max_weight = e if e > max_weight
    end
    
    max_weight
end
```