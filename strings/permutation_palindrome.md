# Permutation palindrome
Write an efficient function that checks whether any permutation of an input string is a palindrome.

## Example
- "civic" should return true
- "ivicc" should return true
- "civil" should return false
- "livci" should return false

## Solution
- Count the number of occurrences of each char and then analyze them
- There must be at max only one odd_pair, all the rest must be even
- If there is more than one odd pair then it cannot be permuted into a palindrome

## Code
```ruby
def is_permutation_palindrome(str)
    char_hash = {}
    str.each_char do |c|
        if char_hash[c]
            char_hash[c] = 0
        else
            char_hash[c] = 1
        end
    end

    odd_pair_seen = false
    char_hash.each do |c, i|
        if i % 2 == 1
            if odd_pair_seen
                return false
            else
                odd_pair_seen = true
            end
        end
    end

    return true
end
```

## Time complexity
- O(n) since we traverse the string once
- O(n) space complexity, since we are storing char counts and occurrence values

