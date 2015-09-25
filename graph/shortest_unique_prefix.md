# Shortest unique prefix
Given a string and a dictionary, find the shortest unique prefix.

## Example
```
Dict = {dog, cur, be}, String = 'cat', Shortest unique prefix = 'ca'
Dict = {dog, car, be}, String = 'cat', Shortest unique prefix = 'cat'
Dict = {dog, cat, be}, String = 'cat', Shortest unique prefix = ''
```

## Soution
- Process the dictionary into a trie, where each node is a letter from each of the strings
- For the given string search the trie one char at a time and keep track of prefix so far
- If at any point the current string is not found in the trie, then the prefix built upto this point
  is the shortest unique prefix

## Code
```ruby
class TrieNode
    leaves = {}
end

class Trie
    attr_accessors :root
    
    def initialize
        root = TrieNode.new
    end
    
    def insert_word(word)
        p = root.leaves
        word.each_char do |c|
            if p[c].nil?
                p[c] = TrieNode.new
            end
            p = p[c].leaves
        end
    end
    
    def find_shortest_prefix()
    end
end

def shortest_unique_prefix(str, dict)
    trie = Trie.new
    dict.each do |word|
        trie.insert(word)
    end
    
    trie.find_shortest_prefix(str)
end
```
