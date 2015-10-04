# Max possible n
Given an unsorted array of integers, you need to return maximum possible n such that the array consists at least n values greater than or equal to n. Array can contain duplicate values.

## Example
```
Sample input : [1, 2, 3, 4] -- output : 2
Sample input : [900, 2, 901, 3, 1000] -- output: 3
```

## Solution
- For every integer between 1..n count them and store in an array
- Now go from n down to 1 and track cumulative count of the counts for each number,
  as soon as cumulative count hits n or higher than n then return that number

## Code
```ruby
def max_n(arr)
    return nil unless arr

    n = arr.size
    count = [0] * n
    arr.each do |e|
        if e < n
            count[e] += 1
        end
    end

    i = count.size - 1
    while i >= 0 do
        cummulative_count += count[i]
        if cummulative_count >= n
            return i
        end
    end
end
```
