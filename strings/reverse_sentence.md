# Reverse sentence
Given a sentence as a string, reverse it.

## Example
```
reverse('Hello world') #=> 'world Hello'
```

## Algorithm
- First reverse the entire sentence
- Then reverse each work in-place

## Code
```ruby
def reverse_word(word)
  left_ptr = 0
  right_ptr = word.size - 1
  while (left_ptr < right_ptr)
    temp = word[left_ptr]
    word[left_ptr] = word[right_ptr]
    word[right_ptr] = temp
    left_ptr += 1
    right_ptr -= 1
  end

  word
end

def reverse_sentence1(sentence)
  result_sentence = ''
  sentence = reverse_word(sentence)
  words_in_sentence = sentence.split(' ')
  words_in_sentence.each do |word|
    result_sentence << reverse_word(word) + ' '
  end

  result_sentence
end
```

## Time complexity
To reverse the entire sentence we are traversing over the string twice (once to reverse the entire sentence and then to reverse each word).
There for O(n+n) = O(n)
