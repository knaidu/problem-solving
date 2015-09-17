# Sequence search in 2D array
Given a 2d array A, and a sequence of numbers S, find if it exists in the array. You are allowed to traverse only up, down, left and right from each cell.

## Example
```
A: 1 2 3 4
   5 6 7 8 

S: 1 2 6 7, Result: true
S: 1 2 3 5, Result: false
```

## Solution
- Use recursion to test of a particular sequence exists starting from each cell in the matrix
- For use an index variable to track where in the sequence we are and how much of the string is left to be compared
- Use a cache to speed up computations, cache would store all the failed indices that we've tried in the past recursions

## Solution
```ruby
class SequenceSearcher
    attr_reader :cache, :a, :s
    
    def initialize(a, s)
        @a = a
        @s = s
        @cache = Set.new
    end

def sequence_search
    return false if @a.nil? || @s.nil?
    
    for i in 0..@a.size do
        for j in 0..@a[0].size do
            return sequence_search_helper(i, j, index)
        end
    end
end

def sequence_search_helper(i, j, index)

    # Reached beyond end of string
    if index == @a.size
        return true
    end
    
    # Check for boundaries or if we've seen this string does not match in earlier recursions
    if cache.find(i,j,index) || i < 0 || j < 0 || i > a.size || j > a.size
        return false
    end
    
    if a[i][j] == s[index] 
       || sequence_search_helper(i+1, j, index + 1)
       || sequence_search_helper(i, j+1, index + 1)
       || sequence_search_helper(i-1, j, index + 1)
       || sequence_search_helper(i, j-1, index + 1)
       return true
    end
    
    cache << {i, j, index} # Indicating failure to find string from this index
    return false
end
```