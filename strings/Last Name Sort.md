# Last Name Sort

Write a function called sortReindeer (sort_reindeer in Ruby) that accepts an array of Reindeer names, and returns an array with the Reindeer names sorted by their last names.

## Example
```
sort_reindeer([
  "Dasher Tonoyan",
  "Dancer Moore",
  "Prancer Chua",
  "Vixen Hall",
  "Comet Karavani",
  "Cupid Foroutan",
   "Donder Jonker",
   "Blitzen Claus"
])
Returns =>
[
  "Prancer Chua",
  "Blitzen Claus",
  "Cupid Foroutan",
  "Vixen Hall",
  "Donder Jonker",
  "Comet Karavani",
  "Dancer Moore",
  "Dasher Tonoyan",
]
```

## Algorithm
1. Modify the string comparator function, in ruby do it with a sort block
2. Or use the sort_by function, that lets you define the sorting parameter

## Code
Approach 1:
```
def sort_reindeer reindeer_names
  reindeer_names.sort do |r1, r2|
    r1.split(' ')[1] <=> r2.split(' ')[1]
  end
end
```

Approach 2:
```
def sort_reindeer(reindeer_names)
  reindeer_names.sort_by{|a| a.split(' ').last }
end
```

## Test cases
```
def solution(array)
  array.sort{|a, b|
    a.split(' ')[1] <=> b.split(' ')[1]
  }
end

reindeerNames = ["Dasher", "Dancer", "Prancer", "Vixen", "Comet", "Cupid", "Donder", "Blitzen"]
lastNames = ["Chua", "Claus", "Foroutan", "Hall", "Jonker", "Karavani", "Moore", "Tonoyan"]
10.times do
  reindeerNames.shuffle!
  lastNames.shuffle!
  testArray = []
  (0...reindeerNames.length).each do |j|
    testArray.push(reindeerNames[j] + ' ' + lastNames[j]);
  end
  Test.assert_equals(sort_reindeer(testArray), solution(testArray))
end
```

## Time complexity
O(n*log n) - assuming its quick sort

