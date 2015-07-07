# Spreadsheet encoding
Given a number encode it into a spreadsheet column title.

## Example
```
1 => A
26 => AA
```

## Solution
- Use mod 26 to get each digit and then convert it into its respective char,
- Divide by 26 until the number is not 0.
- Handle the case with Z seperately.

## Code
```ruby
def encoding(num)
  return '' if num == 0

  result = ''
  while num > 0
    digit = num % 26

    if digit == 0
      result = "#{result}Z"
      num = num / 26 - 1
    else
      value = 'A'.ord + digit - 1
      puts "value: #{value}"
      result = "#{result}#{value.chr}"
      num = num / 26
    end


  end

  result.reverse
end
```

## Complexity
O(n) where n is the number of chars in the column name.

