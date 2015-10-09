# Word break
Given a set of words concatenated together, break them apart.

## Solution
- Keep an array to keep track of all breaking points and the length to break them by
- Start from index 0 and check if 0..i is a valid word, if it is then mark T[i] = i + 1, this is the first word
- Now check j = 0..i for any previous word breaks that were identified
    -  if T[j] != 0 and if str[j+1..i] is a valid word, then set T[i] = i-j
    -  repeat this until end of the string
    
## Code
```ruby
def word_break(str)
    for i in 0..str.len do
        # Find first word
        if valid_word?(str[0..i])
            T[i] = i+1
        end
    
        # Find subsequent words till end of the string
        for j in 0..i do
            if T[j] != 0 && valid_word?(str[j+1..i])
                T[i] = i-j
            end
        end
    end
    
    # Print words as sentences
    i = t.size
    while i>=0 
        if i != 0
            result << str[i-t[i]..i] # extract word
        end
        i -= 1
    end
end
```

## Time Complexity 
O(n^3)