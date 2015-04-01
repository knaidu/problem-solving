# Word cloud data
Write code that takes a long string and builds its word cloud data in a hash map, where the keys are words and the values are the number of times the words occured.

## Example
```
Input: "After beating the eggs, Dana read the next step:")
Output: {"after"=>1, "beating"=>1, "the"=>2, "eggs"=>1, "dana"=>1, "read"=>1, "next"=>1, "step"=>1}
```

## Algorithm
- Scan one character at a time
    - If its an valid char, then append to current word
    - If its a delimiter then push current word to hash and skip over the delimiter
- Handle corner cases carefully
    - Hyphenated word
    - Multiple delimiters
    - Capitalized words

## Code
```
class WordCloud
  attr_reader :text, :word_count_hash

  def self.create(text)
    @text = text
    @word_count_hash = {}
    self.process
  end

  def self.is_letter(c)
    'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.include?(c)
  end

  def self.is_delimiter(c)
    '.,-: '.include?(c)
  end

  def self.add_to_hash(word)
    if @word_count_hash[word]
      count = @word_count_hash[word]
      @word_count_hash[word] = count + 1
    else
      @word_count_hash[word] = 1
    end
  end

  def self.process
    current_word = ''

    for i in 0..@text.size-1
      c = @text[i]
      if self.is_letter(c)
        current_word += c

      elsif self.is_delimiter(c)
        self.add_to_hash(current_word.downcase) unless current_word == ''
        current_word = ''
      end
    end

    self.add_to_hash(current_word) unless current_word == ''

    puts "Hash: #{@word_count_hash}"
  end
end
```

## Test cases
```
WordCloud.create("After beating the eggs, Dana read the next step:")
WordCloud.create("Hello Hello World")
WordCloud.create("Hello Hello.. World World    .... hello--world")

```

