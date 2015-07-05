# Compute parity
Given an integer compute its parity (number of set bits). for negative numbers the MSB will be set,
take that into account while counting set bits.

## Example
```
parity(3)  #=> 2
parity(7)  #=> 3
parity(-7) #=> 4
```

## Solution
- Loop through all the bits and count the set bits
- Trick to improve time complexity is to skip over all the 0-bits by using num = num & (num -1)
  to delete the lowest set bit from the number

## Code
```ruby
def parity(num)
  return 0 if num == 0
  return 1 if num == 1

  if num < 0
    num = -num
    count = 1
  else
    count = 0
  end


  while(num > 0)
    count += 1
    num = num & (num - 1)
  end

  count
end
```

## Completxity
O(k) time, where k is the number of set bits

