# Test if palindrome
Given a string test if its a palindrome

## Example
```
hello => false
madam => true
```

## Solution
- Maintain two pointers, one from the start of the string and the other from the end of the string
- Compare the chars if they are equivalent then increment the left_ptr and decrement the right_ptr until they meet at the center

## Code
```ruby
def is_palindrome(s)
  return true if s.length == 1

  if s.length == 2
    return s[0] == s[1]
  end

  i = 0
  j = s.length - 1

  while i < j
    if s[i] != s[j]
      return false
    else
      i += 1
      j -= 1
    end
  end

  return true
end
```
