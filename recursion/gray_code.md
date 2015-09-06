# Gray code
Given number of bits, generate gray codes for it. Gray code has the property that consecutive numbers differ by one bit and they also wrap around.

## Example
```
n = 2: 00, 01, 11, 10, 00
n = 3: 000, 100, 101, 111, 110, 010, 011, 001
```

## Solution
- Use the result from gray code from num-1 bits, then prepend 0 to the numbers to obtain first half
- Then prepend 1 to the reversed result to ensure there is no number that differs by more than 1 bit
- This also ensures the numbers wrap around accurately without breaking the gray code property

## Code
```ruby
def generate_gray_code(num_bits)
    return [0] if num_bits == 0
    return [0,1] if num_bits == 1
    
    prev_result = generate_gray_code(num_bits-1)
    result = []
    
    # Prepend 0 to existing result and add to result array
    # No action to be taken to add 0, its implicit
    result.push(prev_result).flatten
    
    # Prepend 1 to the reverse of the prev_result
    # Must be reversed to preserve gray property
    prepend_1 = 1 << num_bits - 1
    
    prev_result.reverse.each do |r|
        result << (prepend_1 + r)  # Eg: 100 + 01 = 010
    end
    
    result
end
```

## Complexity
Since we are generating all possible combinations of bits for a given n, (irrespective of the order), it takes 2^n to generate all combinations of numbers for num digits n.