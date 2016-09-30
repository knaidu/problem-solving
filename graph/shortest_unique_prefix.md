# Shortest unique prefix

Given a string and a dictionary, find the shortest unique prefix.

## Example

```
Dict = {dog, car, be}, String = 'cat', Shortest unique prefix = 'ca'
Dict = {dog, cat, be}, String = 'cat', Shortest unique prefix = 'cat'
Dict = {dog, cat, be}, String = 'cat', Shortest unique prefix = ''
```

## Soution

* Process the dictionary into a trie, where each node is a letter from each of the strings
* For the given string search the trie one char at a time and keep track of prefix so far
* If at any point the current string is not found in the trie, then the prefix built upto this point
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
        leaves = root.leaves
        node = root
        # For each char insert a node in the trie
        word.each_char do |c|
            # If char does not exist insert it
            # else just proceed to the node's children
            if leaves[c].nil?
                leaves[c] = TrieNode.new
                node.leaves = leaves
            end
            node = leaves[c]
            leaves = leaves[c].leaves
        end
    end

    def find_shortest_prefix(word)
        leaves = root.leaves
        node = root
        prefix = ''
        word.each_char do |c|
            prefix += c
            if leaves[c].nil?
                return prefix
            end
            leaves = leaves[c].leaves 
            node = leaves[c]
        end
    end

    def find_longest_common_prefix()
        leaves = root.leaves
        prefix = ''
        if leaves.size > 1
            return prefix
        node = root
        q = Queue()
        q.push(leaves)
        while !q.empty()
            x = q.pop()
            if x.leaves.size > 1
                prefix += x.value
                x = x.leaves[0]
            else
                return prefix        
end

def shortest_unique_prefix(str, dict)
    # Create a trie and insert words from dict into it
    trie = Trie.new
    dict.each do |word|
        trie.insert(word)
    end

    trie.find_shortest_prefix(str)
end
```

