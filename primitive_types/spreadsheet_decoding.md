# Spreadsheet decoding
Given a spreadsheet column string like AA, AZ etc, decode it into its numeric value.

## Example
```
AA => 27
Z => 26
```

## Solution
- Use the mod 26 approach to decode the string

## Code
```ruby
def spreadsheet_decoding(str)
    return if str.nil?

    value = 0
    str.each_char do |c|
        value = value * 26 + c - 'A' + 1
    end
end
```

## Complexity
Time: O(n) - where n is the number of chars in the column string
