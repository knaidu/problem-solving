# Combinations of strings with ?
Given a string that contains n '?' in it, ? can be replaced with either 0 or 1. Print all
possible combinations of the string

## Example
```
Input : a?b?c?
Output: a0b0c0, a0b0c1, a0b1c0, a0b1c1, a1b0c0, a1b0c1, a1b1c0, a1b1c1
```

## Solution
- All combinations should ring a bell
- Use the same algo to print all possible combinations of chars for upper and lower case
- Essentially there can be 2^n combinations (n being number of ?s)
- Which can be enumerated as numbers from 000...111 (in bit representation)

## Code
```ruby
def print_combinations(str)
    # Parse string and figure out positions of '?'

    pos = []
    temp = str
    str.each_char.with_index do |c, i|
        if c == '?'
            pos << i
            temp[i] = '0'
        end
    end

    result = [temp] # First string has all ? as 0s

    for i in 1..pos.size do
        temp = str
        while pos.each do |p|
            if i & 1
                temp[p] = '1'
            else
                temp[p] = '0'
            end
            i >> 1
        end
        result << temp
    end
end
```
