# Find duplicate
Given an array that has elements in the range 1..n. There is 1 duplicate element in it. Find the duplicate element using only O(1) space.

## Example
```
i/p: 2,4,6,4,5,1,3
o/p: 4 => duplicate element
```

## Solution
- Key here is to use the fact that there unique positions for each element except the duplicate. 
- Hypothetically if we sort it then we can find the duplicate element. Lets achieve this using a counting approach.
- Use binary search technique, divide the problem into sub-problems at each step by counting which half has more elements than the number of positions.
- For example:

```
array: [2,4,6,4,5,1,3]
1st half: 2,4,6,4
2nd half: 5,1,3,7
1st half of a hypothetically sorted array would be: 1,2,3
So we narrow our search in the first half of the array in the next iteration
```

## Code
```ruby
def find_duplicate(a)
  low = 0
  high = a.size - 1
  mid = (low + high ) / 2

  while (low < high)
    expected_lower_count = mid - low
    actual_lower_count = 0

    a.each do |e|
      actual_lower_count + = 1 if e < mid && e > low

      if expected_lower_count > actual_lower_count
        # Search in the first half
        high = mid
      else
        # Search in the second half
        low = mid
      end
    end
  end

  return mid
end
```
