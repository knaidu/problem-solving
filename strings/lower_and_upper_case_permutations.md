# Lower and upper case permutations
Given a string generate all permutations where each char is lower and upper case

## Example
```
Input: abc
Output: ABC, ABc, AbC, Abc, aBC, aBc, abC, abc
```

## Solution
- Trick is to notice that there are 2^n such permutations, where n is the length of the string
- It maps to
```
111    ABC
110    ABc
101    AbC
100    Abc
011    aBC
010    aBc
001    abC
000    abc
```
- Use 2 loops, outer loop loops over each of the integers from 0 -> 2^n
- Inner loop loops over each char in the string, if the corresponding bit is set then change to
  upper case, otherwise leave it as lower case

## Code
```ruby
def generate_permutations(str)
    return nil if str.nil?

    result = []
    range = 2 ^ str.len
    for i in 0..range do
        temp_str = str
        for j in 0..str.len do
            temp_str[j] = is_bit_set?(i, j) ? temp_str[j].to_upper : temp_str[j]
        end
        result << temp_str
    end
end

def is_bit_set?()
    i >> j && 1 == 1
end
```

