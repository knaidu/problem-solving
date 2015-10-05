# Anagrams

Write a function that will accept a jumble of letters as well as a dictionary, and output a list of words that the match in the dictionary.

## Example
```
grabscrab("ortsp", ["sport", "parrot", "ports", "matey"]) # => ["sport", "ports"
```

## Algorithm
Approach 1:
1. Iterate over the dictionary
2. For every word, sort it and compare with the sorted anagram input
3. If they match add it to the result array, else skip it

Approach 2:
1. Process the dictionary into a hash table
2. Key: sorted word from the dictionary
3. Value: array of a list of anagrams that exist in the dictionary
4. Now for the input anagram, sort it and look up in this hash table

## Code
Approach 1:
```ruby
def grabscrab(anagram, dictionary)
  dictionary.select{|w| anagram.chars.sort == w.chars.sort}
end
```
Approach 2:
```ruby
def grabscrab anagram, dictionary
  indexed_dictionary = process_dictionary(dictionary)
  result = []
  if indexed_dictionary[anagram.chars.sort.join]
    result = indexed_dictionary[anagram.chars.sort.join]
  end

  result
end

def process_dictionary(dictionary)
  indexed_dictionary = {}
  dictionary.each do |word|
    sorted_word = word.chars.sort.join
    word_array = indexed_dictionary[sorted_word]
    if word_array
      word_array << word
      indexed_dictionary[sorted_word] = word_array
    else
      indexed_dictionary[sorted_word] = [word]
    end
  end

  indexed_dictionary
end
```

## Test cases
```
Test.expect(grabscrab("trisf", ["first"]) == ["first"])
Test.expect(grabscrab("oob", ["bob", "baobab"]) == [])
Test.expect(grabscrab("ainstuomn", ["mountains", "hills", "mesa"]) == ["mountains"])
Test.expect(grabscrab("oolp", ["donkey", "pool", "horse", "loop"]) == ["pool", "loop"])
Test.expect(grabscrab("ortsp", ["sport", "parrot", "ports", "matey"]) == ["sport", "ports"])
Test.expect(grabscrab("ourf", ["one","two","three"]) == [])
```

## Time complexity
Approach 1:
- O(n) to iterate over the dictionary
- O(m*logm) to sort each word
- Total: O(n * mlogm)
- Better for 1 time lookups

Approach 2:
- O(n) additional space for the hash table
- Same time complexity as approach 1
- Better for repeated lookups, since they will be O(1)

