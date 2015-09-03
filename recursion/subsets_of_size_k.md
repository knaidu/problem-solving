# Subsets of size k
Given a set, generate all subsets of size k

## Example
```
Input: {1,2,3}, k = 2
Output: {1,2}, {1,3}, {2,3}
```

## Solution
- Remove first element, then recursively generate subsets for the remaining set for size k-1
- Add the result of recursion to the current element to yield a subset of size k

## Code
```ruby
def generate_k_subsets(set, k)
    result = []
    partial_result = []
    generate_subset(set, k, result)
end

def generate_subset(set, k, offset, partial_result result)
    if partial_result.size == k
        result << partial_result
        return result
    end

    i = offset
    num_remaining = k - partial_result.size
    while i < set.size && num_remaining < n-i
        partial_result << set[i]
        result = generate_subset(set, k-1, offset+1, partial_result, result)
        partial_result.pop
    end
end
```
