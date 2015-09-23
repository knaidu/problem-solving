# Justify text
Given an array of words and the length of each line, justify text such that each line begins with a word, and ends with a word with multiple spaces between words if required. The spaces between words must be equally distributed with the excess towards the start of the line.

## Solution
- Use look ahead technique to decide which words should be inserted for current line
- Once the lookahead_length is equal to the line length or just exceeds it, form a line with the current set of words.
- If it has not exceeded then we can add more words to the current line
- For justifying each line, use the number of spaces and distribute them between the words, calculate the space by dividing total number of spaces by the number of words and take the ciel value.

## Code
```ruby
def justify_text(words, line_length)
    
end
```