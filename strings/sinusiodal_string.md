# Sinusiodal string
Given a string, print it sinusiodally.

## Example
```
ip: Hello_world
op:
 e   _   l
H l o w r d
   l   o
```

## Solution
- Observe the pattern of the letters
- first row is: str[1], str[5], str[9], ..
- second row is: str[0], str[2], str[4], ..
- third row is: str[3], str[7], str[11], ..
- Loop through the string and extract these specific chars and push into a result string

## Code
```ruby
def sinusiodal_string(str)
  result = ''
  i = 1
  while i<str.size
    result << str[i]
    i += 4
  end

  i = 0
  while i<str.size
    result << str[i]
    i += 2
  end

  i = 3
  while i<str.size
    result << str[i]
    i += 4
  end

  result
end
```

## Time complexity
O(n + n + n) = O(n), three loops through the string.
Can be optimized into a single loop and approprately storing the 3 rows of strings.
