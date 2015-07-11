# Compute random permutation
Given an array compute a random permutation. The permutation must be equally likely
among the n! permutations generated.

## Solution
- Hint: Use the random subset trick from 'offline sampling algorithm'

## Code
```ruby
def random_permutation(arr)
    i = 0
    while i < arr.size
        r = random(i, arr.size)
        swap(arr, i, r)
        i += 1
    end

    return arr
end
```

## Time complexity
O(n)
