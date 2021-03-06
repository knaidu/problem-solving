# Justify text
Given an array of words and the length of each line, justify text such that each line begins with a word, and ends with a word with multiple spaces between words if required. The spaces between words must be equally distributed with the excess towards the start of the line.

## Solution
- Use look ahead technique to decide which words should be inserted for current line
- Once the lookahead_length is equal to the line length or just exceeds it, form a line with the current set of words.
- If it has not exceeded then we can add more words to the current line
- For justifying each line, use the number of spaces and distribute them between the words, calculate the space by dividing total number of spaces by the number of words and take the ceil value.

## Code
```ruby
def justify_text(words, line_length)
    return nil if words.nil? || line_length == 0
    
    curr_line_length = 0
    curr_words_count = 0
    
    i = 0
    while i < words.size do
        curr_words_count += 1
        
        look_ahead_length = words[i].size + curr_line_length + curr_words_count -1 #(num_blanks)
        
        if look_ahead_length == line_length
            result << create_line(words, i - curr_words_count, i, line_length-curr_line_length)
            curr_words_count = 0
            curr_line_length = 0
        elsif look_ahead_length > line_length
            result << create_line(words, i - curr_words_count-1, i, line_length-curr_line_length)
            curr_words_count = 0
            curr_line_length = 0
        else #look_ahead_length < line_length
            curr_line_length += words[i].size
        end
    end
    
end

def create_line(words, start, end, num_spaces)
    i = start
    str = ""
    num_words = end-start
    while i <= end
        spaces = Math.ceil(num_spaces/(num_words))
        str << words[i] 
        spaces.times do
            str << " " 
        end
        num_spaces = num_spaces - spaces
        num_words -= 1
    end
    
    return str
end
```

## Time complexity
O(n) to build final string and justify the text