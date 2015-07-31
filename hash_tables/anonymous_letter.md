# Anonymous letter
You are given a magazine and a letter. Determine if all the characters in the letter are
constuctable using only the letters from the magazine.

## Solution
- Process the chars in the letter into a hash map
- Now parse the chars in the magazine into a hash, if the count is reached for a paritcular letter,
  then remove it from the hash.
- At any point if the hash has become empty then we are done, return true
- Else after processing the entire magazine if there are any chars remaining in the hash,
  then return false.
- We could do the reverse to reduce complexity but use up more space. The asumption here is the
  letter must be smaller than the magazine for it to be valid.

## Code
```ruby
def can_construct_anonymous_letter(magazine, letter)
    return false if magazine.size < letter.size

    hash = {}
    letter.each_char do |c|
        if hash[c].nil?
            hash[c] = 1
        else
            hash[c] += 1
        end
    end

    magazine.each_char.do |c|
        return true if hash.empty?
        if hash[c] == 0
            hash.remove(c)
        elsif hash[c] == 0
            hash[c] -= 1
        end
    end

    return true if hash.empty?

    # Non-empty hash means some of the chars were not present in the magazine
    return false
end
```

## Complexity
- Time: O(m + n) to process both the magazine and letter
- Space O(n), the number of chars in the letter
