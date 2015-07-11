# Next permutation
Given an array of integers, find the next largest permutation when the permutations are
dictionary ordered.

## Example
```
[1,0,3,2] => [1,2,0,3]
```

## Solution
- Notice that the next largest permutation must be done only by swapping
- Find the longest decreasing suffix, k..n
- k-1th element is the one that must be swapped with an element in k..n that is next largest to k
- Reverse the elements in the k..n suffix so that it represents the next largest

## Code
```ruby
def next_largest_permutation(arr)
    ## Find longest decreasing suffix
    i = arr.size - 1
    while i >= 0
        if arr[i] < arr[i+1]
            i -= 1
        else
            break
        end
    end

    ## Find the element to be swapped
    if i<=0  # No larger permutation exists
        return arr
    else
        k = i-1
    end

    ## Swap k with the next largest in longest decreasing suffix
    i = arr.size - 1
    while i>k
        if arr[i] > arr[k]
            swap(arr, i, k)
            break
        else
            i -= 1
        end
    end

    ## Reverse the longest decreasing suffix
    arr = reverse(arr, k, n)

    ## Return the next largest permutation
    return arr
end
```

## Time complexity
O(n)
