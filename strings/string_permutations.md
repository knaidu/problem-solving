# String permutations
Write a recursive function for generating all permutations of an input string

## Example
```
i/p: cat
o/p: ["tac", "atc", "act", "tca", "cta", "cat"]
```

## Solution
- Think of solving this with a string without the last char and then appending the last char in every possible position in the string
- Recursively implement this for string lengths of all sizes

## Code
```ruby
def get_permutations(str)

  return [str] if str.size == 1

  last_char = str[str.size-1...str.size]
  str = str[0...str.size-1]

  permutations_except_last = get_permutations(str)

  permutations = []

  permutations_except_last.each do |str|
    i = 0
    while i <= str.size do
      result = str[0...i] + last_char + str[i...str.size]
      permutations << result
      i += 1
    end
  end

  permutations
end
```

## Time complexity
O(n*n!), n! for producing permutations of a string, repeating this n times per substring+last char combination.
