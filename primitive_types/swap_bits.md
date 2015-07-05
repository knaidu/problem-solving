# Swap bits
Given an integer and incices of 2 bits, swap the bits.

## Solution
- First determine if the bits must be swapped,
    - If they are the same no need to swap
    - If they are not the same, then just flip the bits

## Code
```ruby
def swap_bits(num, i, j)
    return 0 if num == 0
    return 1 if num == 1

    bit_at_i = (num >> i) & 1
    bit_at_j = (num >> j) & 1

    if bit_at_i != bit_at_j
        num = (1 << i) ^ num
        num = (1 << j) ^ num
    end

    return num
end
```

## Time complexity
O(n) where n is the number of bits in the integer (32 or 64).
