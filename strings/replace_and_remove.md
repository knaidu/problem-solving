# Replace and remove
Write a function which takes as input a string s, and removes each "b" and replaces each "a" by "dd". Use 0(1) additional storage-assume s is stored in an array that has enough space for the final result

## Solution
- The constraint here is space. The trick is knowing there is extra space at the end of the string to accommodate the result string after computation.
- Start parsing the string from the last char and insert the result chars towards the end of the string.

## Code
```ruby
i = find_last_char(str)
j = str.length -1

while i >= 0
    if str[i] == 'b'
        i -= 1
    elsif str[i] == 'a'
        str[j] = 'd'
        j -= 1
        str[j] = 'd'
        j -= 1
    else
        str[j] = str[i]
        j -= 1
        i -= 1
    end
end

return str
```

## Time complexity
O(n) since we're traversing the string only once
