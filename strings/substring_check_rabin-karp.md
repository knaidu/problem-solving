# Substring check Rabin-Karp
Given 2 strings t and s, check if s is a substring of t. Use the linear time Rabin-Karp
algorithm instead of the O(m*n) brute force algorithm

## Solution
- Rabin-Karp is similar to brute force, except it uses a fingerprint check instead of
  examining the substring at ever index of t.
- The finger print could be a hash of sorts
- Here we use a simple hash that represents s and t's substring so they can be compared

## Code
```ruby
def is_substring(t, s)
    return false if t.nil? || s.nil?
    return false if t.size < s.size

    t_hash = 0
    s_hash = get_rolling_hash(s_hash, s)

    for i in (0..t.size - s.size) do
        t_substring = t[i...i+s.size]
        t_hash = get_rolling_hash(t_hash, t_substring)

        # Check if there is a potential match
        return t_substring == s if s_hash == t_hash
    end

    # Compare the tail end of t
    return true if t[t.size-s.size...-1] == s

    # There was no substring match
    return false
end

# Use ascii value of each char for hash computation
# hash('abc') = (97 * 10 + 98 * 10 + 99 * 10) mod 100
def rolling_hash(hash, str)
    magic_mod_value = 100
    if hash != 0
        hash = hash - str[0].ord
        hash *= 10
        hash += str[-1].ord
        hash %= magic_mod_value
    else
        str.each_char do |c|
            hash += c.ord
            hash *= 10
        end
        hash %= magic_mod_value
    end

    return hash
end
```

## Time complexity
The brute force algorithm was O(m*n) here we are avoiding the extra substring comparison by
computing fingerprint and comparing them instead which ideally is O(1) (depends on the
hash function). Therefore time complexity of this algorithm is O(n).
