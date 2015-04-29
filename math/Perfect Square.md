# Perfect Square

Given an array of numbers return an array of numbers from the array that qualify as perfect squares. A perfect square is defined as a whole number that, when square rooted, is a whole number. (Such as 1, 4, 9, 16, etc, etc.)

## Example
```
get_squares(1..16) # => [1, 4, 9, 16]
get_squares(1..100) # => [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

## Algorithm
1. Iterate over the array and test each element if its a perfect square
2. Take square root of the number and check if the number has any decimal portion by doing: (element % 1)


## Code
```ruby
def get_squares(array)
  array.select{ |i| Math.sqrt(i) % 1 == 0 }.uniq.sort
end
```

## Test Cases
```
describe "Example Tests" do
  Test.assert_equals(get_squares((1..16)), [1,4,9,16])
  Test.assert_equals(get_squares((1..100)), [1,4,9,16,25,36,49,64,81,100])
  Test.assert_equals(get_squares([4,1,16,1,10,35,22]), [1,4,16])
end

describe "Range Tests" do
  Test.assert_equals(get_squares((1..4)), [1,4])
  Test.assert_equals(get_squares((25..100)), [25,36,49,64,81,100])
  Test.assert_equals(get_squares((7..20)), [9,16])
  Test.assert_equals(get_squares((10000..10001)), [10000])
end

describe "Unsorted Tests" do
  Test.assert_equals(get_squares([4,1]),                [1,4])
  Test.assert_equals(get_squares([36,25,49,81,64,100]), [25,36,49,64,81,100])
  Test.assert_equals(get_squares([16,2,3,16,4]),        [4,16])
  Test.assert_equals(get_squares([4,64,36,22,16]),       [4,16,36,64])
end

describe "Unique Tests" do
  Test.assert_equals(get_squares([4,4,4,4,1,1,1,1]),          [1,4])
  Test.assert_equals(get_squares([4,4,4,2,2,16,36,2]),        [4,16,36])
  Test.assert_equals(get_squares([9,4,4,4,3,2,2,2,16]),       [4,9,16])
  Test.assert_equals(get_squares([64,64,2,2,2,2,16,4,36,36]), [4,16,36,64])
end
```

## Time Complexity
- Iterating over the array O(n)
- Testing perfect square O(1)
- Verifying if it exists in the array O(n), but can be improved with a hash table O(1)
- Sorting the array O(n*log n)
