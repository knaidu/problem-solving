# Temperature tracker
Write a class TempTracker with these methods:

- insert()—records a new temperature
- get_max()—returns the highest temp we've seen so far
- get_min()—returns the lowest temp we've seen so far
- get_mean()—returns the mean of all temps we've seen so far
- get_mode()—returns the mode of all temps we've seen so far

Optimize for space and time. Favor speeding up the get_ functions over speeding up the insert() function.

## Solution
- Hint: all the temperatures need not be stored
- We can calculate min, max on the fly
- We'll need to store sum and count to calculate mean
- For mode, we'll have to store occurrences and keep track of the number with max occurrence

## Code
```ruby
# The crux of the the problem is in the insert method, rest of the code is straightforward

def insert(temperature)

    # for mode
    if @temperature_hash[temperature]
      @temperature_hash[temperature] += 1
      if @temperature_hash[temperature] > @max_occurrence
        @max_occurrence = @temperature_hash[temperature]
        @mode = temperature
      end
    else
      @temperature_hash[temperature] = 1
    end

    # for min and max
    @max = temperature if temperature > @max
    @min = temperature if temperature < @min

    # for mean
    @sum += temperature
    @count += 1
    @mean = @sum/@count
  end
```

## Time complexity
- O(1) for all operations
