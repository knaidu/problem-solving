# Say and Tell
Given a seed array, return a "say and tell" array
A say and tell array first lists the count of the element in the original array and then lists the element itself

### Example
```
[1,2,3] #=> [1,1, 1,2, 1,3]
```

## Algorithm
1. Iterate over the array
2. Keep track of the count of every element
3. Iterate over unique elements in the array and generate the say and tell array

## Code
```
def say_and_tell(seed_array)
  raise ArgumentError, "Invalid input, seed array must have at least 1 element" unless seed_array.size > 0
  compute_result_from(seed_array, count_elements_in(seed_array))
end

def count_elements_in(seed_array)
  count_hash = {}
  seed_array.each { |num| count_hash.include?(num) ? count_hash[num] += 1 : count_hash[num] = 1 }

  count_hash
end


def compute_result_from(seed_array, count_hash)
  result_array = []
  seed_array.uniq.each { |num| result_array << count_hash[num] << num }

  result_array
end
```

## Test cases
```
say_and_tell([1,2,3]) # => [1,1,1,2,1,3]
say_and_tell([1,1,1,1,1,1,1,2,2,2,2,2,3,3,3]) # => [7, 1, 5, 2, 3, 3]
say_and_tell([]) # => ArgumentError: Invalid input, seed array must have at least 1 element
```

### Time complexity
1. O(N) to iterate over the array and count elements
2. O(N) to generate uniq array
3. O(N) to generate final result
