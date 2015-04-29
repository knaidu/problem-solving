# Unique Integer
Given the array of IDs, which contains many duplicate integers and one unique integer, find the unique integer. All integers have one duplicate except the unique integer.

## Example
```
Input => [1,1,2,2,3,3,4]
Output => 4
```

## Algorithm
- Use the XOR operator, it cancels out the bits when an integer is XOR'd with itself
- XOR all the elements of the array
- The remainder will be the unique number in the array

## Code
```ruby
def uniq_integer(input_array)
  unique = 0
  input_array.each do |num|
    unique = unique ^ num
  end

  unique
end
```

## Test cases
```
uniq_integer([1,1,2,2,3,3,4]) #=> 4
uniq_integer([1,1,2,2,3,3,4,3,3]) #=> 4
uniq_integer([1,1]) #=> 0
```

## Time complexity
- Visiting each element only once, therefore O(n)
- Using only O(1) space
