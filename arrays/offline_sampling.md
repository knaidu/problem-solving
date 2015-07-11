# Offline sampling
Given an array of integers, return a random subset of k randome integers. Use as few calls to
random() as possible. All subsets should be equally likely.

## Solution
- Pick a random integer from the array at random
- To ensure the number is not repeated, swap the picked number towards the start,
  in the next picking reduce the range of integers to pick from

## Code
```ruby
def offline_sampling(arr, k)
    i = 0
    result = []
    while i<k
        r = random(i, k)
        result << arr[r]
        swap(arr, i, r)
        i += 1
    end

    return result
end
```

## Time complexity
O(n)
