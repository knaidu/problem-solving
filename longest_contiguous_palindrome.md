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
def longest_palindrome(str, start_index, palindrome)
  return palindrome if str.nil?

  if start_index == str.size
    return palindrome
  end

  if palindrome.size > str.size - start_index 
    return palindrome
  end

  i = start_index
  while i < str.size do
    prefix = str[start_index..i]
    puts "#{prefix}"
    if is_palindrome(prefix)
      if prefix.size > palindrome.size        
        palindrome = prefix
      end
    end
    i += 1
  end

  start_index += 1
  palindrome = longest_palindrome(str, start_index, palindrome)

  return palindrome
end

def is_palindrome(str)
  str == str.reverse
end
```

## Optimizations
- Short circuit the recursion if at any point we cannot form strings longer than the palindrome discovered so far
- Instead of incrementally building the string, start with the longest string possible and incrementally trim the string. This ensures we find the longest palindrome earlier in the search, than later. But overall complexity remains the same.

## Complexity
- For every index we are searcning through all possible strings starting at that index, which takes O(n). Therefore overall time complexity O(n^2).

