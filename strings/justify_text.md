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
    return nil if words.nil? || line_length == 0
    
    curr_line_length = 0
    curr_words_count = 0
    
    for i in 0..words.size do
        curr_words_count += 1
        
        look_ahead_length = words[i].size + curr_line_length + curr_words_count -1 #(num_blanks)
        
        if look_ahead_length == line_length
            result << create_line(words, i - curr_words_count, i, curr_words_count)
            curr_words_count = 0
            curr_line_length = 0
        elsif look_ahead_length > line_length
            result << create_line(words, i - curr_words_count-1, i, curr_words_count-1)
        else #look_ahead_length < line_length
            curr_line_length += words[i].size
        end
    end
    
end

def create_line(words, start, end, num_words_in_line)

end

```