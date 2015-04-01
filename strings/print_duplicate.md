# Print Duplicate
Print only the duplicate chars in the given string.

## Example
```
Input: Hello World
Output: lo
```

## Algorithm
- Loop through all chars in the string
- Use a Set data structure to keep track of the chars seen so far
    - When visiting each char, if the char is already in the set then report as duplicate,
    - Else append it to the set

## Code
```
require 'set'

class PrintDuplicate
  def initialize(text)
    @text = text
    @char_set = Set.new()
    @duplicates = ''
    report_duplicate
  end

  def report_duplicate
    @text.each_char do |c|
      c = c.downcase
      @char_set.include?(c) ? @duplicates += c : @char_set.add(c)
    end

    @duplicates
  end
end

puts PrintDuplicate.new("test")
```

## Test cases
```
PrintDuplicate.new("lL") #=> 'l'
PrintDuplicate.new("tesT") #=> 't'
PrintDuplicate.new("tesT121") #=> 't1'
```

## Time complexity
O(n), since we are looping over the string just once.
Checking set membership is just O(1)
