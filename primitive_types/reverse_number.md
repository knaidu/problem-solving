# Reverse number
Given an integer, reverse it.

## Solution
- The technique here is to extract one digit at a time from the right to left of the integer
- Take each digit and insert it in the opposite order in the result number
- Handle negative numbers appropriately

## Code
```ruby
def reverse(num)
  return num if num == 0

  if num < 0
    is_negative = true
    num = -num
  end

  result = 0
  while num != 0
    digit = num % 10
    num = num / 10
    result = result * 10 + digit
  end

  is_negative ? -result : result
end
```

## Time complexity
O(n) where n is the number of digits in the integer
