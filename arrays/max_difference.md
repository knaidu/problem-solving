# Max Difference
Design an algorithm that determines the maximum profit that could have been made by buying and then selling a single share over a given day range, subject to the constraint that the buy and the sell have to take place at the start of the day.

## Example
```
compute_max_diff([1,2,3,4,5,6,7,8,9]) # => 8
```

## Algorithm
- Keep a running counter of the max_diff_so_far
- Keep a running counter of the min_so_far
- Run through the entire array
- Once all elements are exhaused the max diff is available in max_diff_so_far

## Code
```ruby
def compute_max_diff(elements)
  max_diff_so_far = 0
  min_so_far = 999
  elements.each do |e|
    max_diff_so_far = [max_diff_so_far, e - min_so_far].max
    min_so_far = [e, min_so_far].min
  end

  max_diff_so_far
end
```

## Test cases
```
compute_max_diff([1,2,3,4,5,6,7,8,9]) # => 8
compute_max_diff([9,1]) # => 0
compute_max_diff([5,15,3]) # => 10
compute_max_diff([5,15,3,20]) # => 17
```

## Time complexity
- O(n), since we are looping over the array only once.
