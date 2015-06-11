# Which appears twice
Given an array where every number in the range 1...n appears once except for one number which appears twice. Write a function to find the number that appears twice.

## Example
```
i/p: [1,2,3,4,5,6,6], 6
o/p: 6
```

## Solution
- Use math instead of searching through the array
- Hint is that the numbers are in the range 1..n
- The difference between expected sum of the range and actual sum is the repeating number

## Code
```ruby
def which_appears_twice(array, n)
  expected_sum = (n * (n+1))/2
  sum = 0

  array.each { |e| sum += e }

  sum - expected_sum
end
```

## Complexity
- O(n) to calculate sum of all numbers in the array
- O(1) extra space to hold expected sum
