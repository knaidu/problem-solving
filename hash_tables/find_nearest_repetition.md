# Find nearest repetition
Write a program that takes input an array and finds the distance between a closest pair of equal
entries.

## Example
```
Input: All work and no play makes jack no a dull no boy no.
Output: 'no' with a distance of 2
```

## Solution
- Use a hash table to store the last position a word was seen
- Each time the word is seen again, calculate the distance from current position
- Keep track for the nearest repetition seen so far
- Update the hash table to now reflect the current position for the word

## Code
```ruby
def neareset_repetition(arr)
    nearest_distance = 999
    nearest_value = ''
    word_hash = {}

    arr.each.with_index do |word|
        word_hash[word] = index unless word_hash[word]

        last_position = word_hash[word]
        distance = index - last_position
        if distance < nearest_distance
            nearest_distance = distance
            nearest_value = word
        else
            word_hash[word] = index
        end
    end

    nearest_value, nearest_distance
end
```

## Complexity
- Time: O(n), parsing over the array only once
- Space O(n), to maintain the hash table with last seen index for every word
