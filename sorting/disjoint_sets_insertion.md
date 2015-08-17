# Disjoint sets insertion
Write a program that takes as input an array of disjoint intervals closed intervals, sorted by increasing order left end-point. How would you insert a new interval such that the final result remains disjoint and sorted.

## Example
```
Input: (-3,-1) (0,2) (3,6) (7,9) (11, 12)
Insert: (1,8)
Result: (-3,-1) (0,9) (11,12)
```

## Solution
- Parse the intervals from left to right and check intersection
- Intersection can be checked by comparing the 4 end points
- If it does not intersect move the disjoint interval to the result array
- If it does intersect then merge them and compare with the next element in the array
- Keep track of the current interval for comparing and merging

## Code
```ruby
class Interval
    attr_accessor :start, :stop

    def initialize(start, stop)
        @start = start
        @stop = stop
    end

    def intersect?(interval)
        @stop >= interval.start && @stop <= interval.stop
    end

    def merge(interval)
        @start = min(@start, interval.start)
        @stop = max(@stop, interval.stop)
    end
end

def insert_interval(intervals, insertion_interval)
    return nil if arr.nil?

    result = []
    merged_interval = insertion_interval
    arr.each do |interval|
        if merged_interval.intersect?(interval)
            merged_interval.merge(interval)
        else
            result << merged_interval
            merged_interval = interval
        end
    end

    result << merged_interval
end
```

## Complexity
- Time: O(n) since we are parsing the arry of intervals just once. It could be sped up by doing
  a binary search for the right merge spot, but the worst time is still O(n) since it may
  potentially required merging the rest of the array if the interval is larger than all the elements
- Space: O(n) for storing the result array, otherwise constant space for processing.

