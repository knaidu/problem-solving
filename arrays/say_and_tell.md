# Look and Say
Find the nth integer in a look and say array starting at 1

## Example
```
Look and say array:
<1, 11, 21, 1211, 111221, 312211, 13112221, 1113213211>
```

## Solution
- Use 2 pointers i and j to keep track of the equal integers
- Increment j until the values in i and j are no longer same
- Use the diff in j-i as the counter
- Do this until we exhaust all integers in the given array
- Repeat above for each step until and feed the result into the next step n times

## Code
```ruby
def find_nth(n)
  a = [1]
  n.times do
    result = look_and_say(a)
    a = result
  end

  return a
end

def look_and_say(a)
  i = 0
  j = 0
  result = []

  while i < a.length
    j += 1 if j < a.length
    if a[i] != a[j]
      result << j-i << a[i]
      i = j
      count = 1
    end
  end

  result
end
```

## Time complexity
- For every step we're iterating through m integers, O(m)
- We're repeating each step n thimes, O(n)
- Overall complexity is: O(m*n)
- m here is mostly finite and can be considered constant.

