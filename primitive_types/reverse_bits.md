# Reverse bits
Given an integer, reverse the bits in it.

## Solution
- Test each LSB bit in the given num and push appropriate bit into the result
- Ensure we're moving in the opposite order while constructing result to make
  the result is reversed.

## Code
```ruby
def reverse_bits(num)
    return 0 if num == 0
    return 1 if num == 1

    result = 0
    while (num > 0)
        value = num & 1
        result << 1
        result = result ^ 1 if value == 1 # Injects 1 at the LSB
        num = num >> 1
    end
end
```

## Complexity
O(n) time, where n is the number of bits in the number.
