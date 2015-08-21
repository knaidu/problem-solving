# Word transformation
Given a starting word s, an ending word t and a dictionary d. Determine if its possible to go from
s to t using the words in the dictionary.

## Solution
- Do a BFS on the hypothetical graph from starting word outwards
- From each word, iterate through the letters in the word one at a time and compute a list
  of all possible 1 char transformations from that word.
- Repeat this until we reach t or run out of nodes to examine

## Code
```ruby
def is_word_transformable(s, t, d)
    q = [s: 0]
    while !q.empty?
        e, count = q.pop
        if e == t
            return true
        end
        one_char_transformation(e).do |word|
            q.insert(word, count+1)
        end
    end

    return false
end

def one_char_transformation(word)
    result = []
    for i in 0..word.size do
        for j in 0..26 do
            if is_valid(d, word[i] = 'a' + j)
                result << word
            end
        end
    end

    result
end
```

## Complexity
- Time complexity: total number of words in the dictionary is d, and max number of edges is d^2
- BFS complexity is O(E+V) = O(d+d^2) = O(d^2)
- Space: O(d)
