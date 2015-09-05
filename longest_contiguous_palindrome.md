# Longest contiguous palindrome
Given a string, find the longest contiguous palindrome.

## Example
```
'racecar' => 'racecar'
'abacabde' => 'bacab'
'abcbebacab' => 'bacab'
```

## Solution
- Start from index 0, build a partial string incrementally, upto end of string
- For each partial string check if its a palindrome, update result if its longer than previously
  found palindrome
- Repeat this at the next index until we have exhaused all indices

## Code
```
def longest_palindrome(str, current_index, palindrome)
  # Base case, when we've exhaused all substrings
  return palindrome if str.nil?

  # Reached end of string
  return palindrome if start_index == str.size

  # Short circuit when we've already found the longest possible palindrome in current iteration
  return palindrome if palindrome.size > str.size - start_index 
    
  # Generate all possible strings starting at current_index
  for i in current_index..str.size do
    partial_string = str[start_index..i]
    if is_palindrome(partial_string)
      palindrome = partial_string if partial_string.size > palindrome.size        
    end
  end

  # Move to next index and recurse until last index
  current_index += 1
  palindrome = longest_palindrome(str, current_index, palindrome)

  return palindrome
end

def is_palindrome(str)
  str == str.reverse
end

# Run 
puts longest_palindrome('racecar', 0, '')
```

## Optimizations
- Short circuit the recursion if at any point we cannot form strings longer than the palindrome discovered so far
- Instead of incrementally building the string, start with the longest string possible and incrementally trim the string. This ensures we find the longest palindrome earlier in the search, than later. But overall complexity remains the same.

## Complexity
- For every index we are searcning through all possible strings starting at that index, which takes O(n). Therefore overall time complexity O(n^2).

