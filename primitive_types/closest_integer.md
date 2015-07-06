# Closest integer
Given an integer, find the closest integer with the same weight. Here weight is defined as the count of set bits in the decimal representation of the integer.

## Example
```
# 0111 => 1011
closest_integer(7) #=> 11:
```

## Code
```ruby
def closest_integer(num)
    for i in 0..64
        # Check if consecutive bits are different
        if (x >> i) & 1 ^ (x >> x+1) & 1 == 1
            # then swap them or flip their bits
            mask = 1 << i | 1 << i+1
            x = x ^ mask
            return x
        end
    end

    raise Exception('All bits are 0 or 1')

end
```

## Complexity
Time: O(n) where n is the number of bits in the given integer (max # of bits)
