# Count frequencies of chars
Given a string of chars, count the frequencies of each char and report them in sorted order

## Solution
- Sort the string and then apply run-length encoding on the sorted string

## Code
```ruby
def count_frequencies(str)
    return nil if str.nil?

    i = 1
    count = 1
    while i < str.size
        if str[i] == str[i-1]
            count += 1
        else
            puts "( #{str[i-1]}, #{count} )"
            count = 1
        end
        i += 1
    end

    puts "( #{str.last}, #{count} )"
end
```

## Complexity
- Time: O(n logn) for sorting and O(n) for counting
- Space: constant (since we didn't use a hash table to count frequencies)
