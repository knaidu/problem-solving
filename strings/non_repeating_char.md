# Non Repeating Char
Given a string, find the first non-repeating character in it.

## Example
```
Input: test
Output: e
```

## Algorithm
- Parse through the given string and build a hash of char frequency and position, e.g {'t' => <5, 0>} meaning char 't' was seen 5 time and the first occurrence was at position 0.
- Parse through this hash and find the char with frequency 1 and lowest position (i.e. the first occurrence)


## Code
```ruby
class NonRepeatingChar
  attr_reader :result

  def initialize(text)
    @text = text
    @char_count_hash = {}
    compute_char_count_and_position
    @result = find_first_non_repeating_char
  end

  def compute_char_count_and_position
    @text.each_char.with_index do |c, i|
      @char_count_hash[c] ? increment_char_count(c) : @char_count_hash[c] = Occurrence.new(1, i)
    end
  end

  def find_first_non_repeating_char
    lowest_position = @text.size
    non_repeating_char = ''
    @char_count_hash.each do |c, occurrence|
      if(occurrence.frequency == 1)
        if (lowest_position > occurrence.position)
          lowest_position = [lowest_position, occurrence.position].min
          non_repeating_char = c
        end
      end
    end

    non_repeating_char
  end

  def increment_char_count(c)
    occurrence = @char_count_hash[c]
    occurrence.frequency += 1
    @char_count_hash[c] = occurrence
  end
end

class Occurrence
  attr_accessor :frequency, :position

  def initialize(frequency, position)
    @frequency = frequency
    @position = position
  end
end


NonRepeatingChar.new('tesla').result
```

## Test cases
```
NonRepeatingChar.new('tesla').result #=> t
NonRepeatingChar.new('teslat').result #=> e
NonRepeatingChar.new('teslate').result #=> s
NonRepeatingChar.new('teslates').result #=> l
NonRepeatingChar.new('teslatesl').result #=> a
NonRepeatingChar.new('teslatesla').result #=> nil
```

## Time complexity
O(n) - to parse the given string
O(n)- to parse the hash in the worst case assuming all chars are unique


