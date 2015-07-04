# Check palindromic number
Given a number test if its a palindrome.

## Example
```
121 #=> true
123 #=> false
```

## Solution
- Either reverse the number or throw the digits into a stack and compare with the original number digit by digit

## Code
```ruby
def check_palindromic_number(num)
  return false if num.nil?

  # Single digit is a palindrome
  return true if num/10 == 0

  stack = []
  num_copy = num

  # Extract digits and push onto stack
  while num_copy != 0
    stack.push(num_copy % 10)
    num_copy = num_copy / 10
  end

  while !stack.empty?
    if stack.pop == num % 10
      num = num / 10
    else
      return false
    end
  end

  return true
end
```

## Time complexity
O(n) since we are traversing over the digits a max of 2 times.
