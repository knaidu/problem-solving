# Boggle game
Given a matrix of chars and a dictionary, list all the valid words that are possible to create
using the given matrix.

## Solution
- Every char in the matrix could be the starting point for a given word
- Use recusion from the chosen location to find the next letter and append to the word_so_far
- Use a visited hash to prevent reusing any of the tiles

## Code
```ruby
class Dictionary
    attr_reader: dictionary

    def initialize(dictionary)
        @dictionary = dictionary
    end

    def exists?(word)
        dictionary.include?(word)
    end
end

def find_words(dictionary, matrix)
    return nil unless dictionary
    return nil unless matrix

    d = Dictionary.new(dictionary)
    visited = {}
    words = []

    for i in 0..matrix.size-1
        for j in 0..matrix[0].size-1
            find_words_helper(d, i, j, matrix, visited, words)
        end
    end

    words
end

def valid(i, j, matrix)
    i >= 0 && i < matrix.size && j >=0 && j < matrix.size
end

def find_word_helper(d, i, j, matrix, visited, words)
    return nil unless valid(i,j, matrix)
    visited[{i,j}] = true if visited[{i,j}] == false

    word_so_far += matrix[i][j]
    words.push(word_so_far) if word_so_far

    # Go all 8 directions
    find_words_helper(d, i-1, j-1, matrix, visited, words, word_so_far)
    find_words_helper(d, i-1, j, matrix, visited, words, word_so_far)
    find_words_helper(d, i-1, j+1, matrix, visited, words, word_so_far)
    find_words_helper(d, i, j+1, matrix, visited, words, word_so_far)
    find_words_helper(d, i+1, j+1, matrix, visited, words, word_so_far)
    find_words_helper(d, i+1, j, matrix, visited, words, word_so_far)
    find_words_helper(d, i-1, j+1, matrix, visited, words, word_so_far)
    find_words_helper(d, i-1, j, matrix, visited, words, word_so_far)

    visited[{i,j}] = false
    word_so_far = word_so_far[0..word_so_far.size-2] # Remove last char
end
```

## Complexity
- Assuming n tiles in the matrix where n is rowXcols
- O(n*n) is the complexity, we doing DFS from each tile n times
