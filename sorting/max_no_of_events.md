# Max no. of events
Given a set of intervals (not necessarily disjoint), write a program that takes a set of events,
and determines the maximum number of events that take place concurrently.

## Example
```
Input: [1,5], [2,7], [4,5], [6,10], [8,9], [9,17]
Output: 3 [4,5]
```

## Solution
- Split the interval by start and end point and then sort them in ascending order.
- Split ties based on start interval
- Now parse through these points, and keep track of maximum number of events seen per interval
  unit.

## Code
```ruby
def max_interval(arr)
    arr = split_by_event(arr)
    arr = arr.sort

    count = 0
    max_interval = 0
    arr.each do |event|
        if is_start_event?(event)
            count += 1
            max_interval = max(max_interval, count)
        else
            count -= 1
        end
    end

    max_interval
end
```

## Complexity
- Time: O(n logn) to sort the array, O(n) to find the max interval
- Space: constant, since the algorithm works in-place
