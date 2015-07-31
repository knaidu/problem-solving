# Parition into anagrams
Given an array of strings, sort them such that the anagrams appear together.

## Example
```
Input: elvis, silent, debitcard, lives, listen, badcredit
Output: elvis, lives, silent, listen, debitcard, badcredit
```

## Solution
- Use a sorting technique to sort them by anagram order
- For the comparator, check if 2 strings are anagrams or not
- Naive technique is to sort both the strings and compare O(n log n)
- Faster approach is to use a hash table, track the num elements and check if they are anagrams

## Code
```ruby
def anagram_order(arr)
    return nil if arr.nil?

    sort(arr, comparator_function)
end

def comparator_function(element1, element2)
    is_anagram(element1, element2)
end

# Return a hash of anagrams
def anagram_map(arr)
    return nil if arr.nil?

    anagrams = {}

    arr.each do |str|
        sorted_str = str.sort
        if anagrams[sorted_str]
            list = anagrams[sorted_str]
            list << s
            anagrams[sorted_str] = list
        else
            list = []
            list << s
            anagrams[sorted_str] = list
    end

    anagrams
end

def is_anagram(str1, str2)
    return false if str1.size != str2.size

    string_hash = {}

    # Count chars in string 1
    str1.each_char do |c|
        if string_hash[c].nil?
            string_hash[c] = 1
        else
            string_hash[c] += 1
        end
    end

    # Check with chars in string 2
    str2.each do |c|
        if string_hash[c].nil?
            return false
        elsif string_hash[c] == 0
            return false
        else
            string_hash[c] -= 1
        end
    end

    true
end
```
