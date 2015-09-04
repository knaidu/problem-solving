# Palindromic decomposition
Given a string n, generate all possible palindromic combinations

## Example
```
Input: ababbaba
Output: a, b, aba, bb
```

## Solution
- Similar to generating k subsets, use recursion to include the first char in the partial result
  and then recurse until we reach the end of the string
- Do this in a loop to include first, first+second and so on, using offsets

## Code
```ruby
def palindromic_decomposition_problem(str)
    partial_result = []
    palindromic_decomposition(str, 0, partial_result)
end

def palindromic_decomposition(str, offset, partial_result)
    if offset == str.size
        return partial_result
    end

    for i in offset..str.size do
        prefix = str[0..i]
        if is_palindrome(prefix)
            partial_result.push(prefix)
            result = palindromic_decomposition(str, i, partial_result)
            partial_result.pop
        end
    end

    result
end
```

## Complexity
O(n * 2^n)

