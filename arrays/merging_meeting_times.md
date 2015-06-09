# Merging meeting times
Write a function condense_meeting_times() that takes an array of meeting time ranges and returns an array of condensed ranges.

## Example
```
i/p: [(0, 1), (3, 5), (4, 8), (10, 12), (9, 10)]
o/p: [(0, 1), (3, 8), (9, 12)]
```

## Solution
- First the meeting times must be sorted by start_time
- Once sorted, traverse the array and check if 2 intervals can be merged or not
- Appropriately merge them and append to the result array

## Code
```ruby
class Interval
  attr_accessor :start, :stop

  def initialize(start, stop)
    @start = start
    @stop = stop
  end
end

# Assuming meeting have already been sorted
def merge(sorted_times)
  return nil if sorted_times.nil?

  merged_meetings = []

  # Start with the first interval and treat it as merged
  merged_start = sorted_times[0].start
  merged_stop = sorted_times[0].stop

  sorted_times.each do |current_interval|
    # if they can be merged, merge them
    if merged_stop > current_interval.start
      merged_stop = merged_stop >= current_interval.stop ? merged_stop : current_interval.stop

    # distinct intervals found, append to result
    else
      merged_meetings << Interval.new(merged_start, merged_stop)
      merged_start = current_interval.start
      merged_stop = current_interval.stop
    end
  end

  # append final interval to the result
  merged_meetings << Interval.new(merged_start, merged_stop)

  merged_meetings
end

sorted_intervals = [Interval.new(1,3), Interval.new(2,4), Interval.new(3,8)]

merge(sorted_intervals).inspect
```

## Time complexity
- O(n log n) to sort the array by start_time
- O(n) to traverse and merge intervals
- O(n) extra space for the result
