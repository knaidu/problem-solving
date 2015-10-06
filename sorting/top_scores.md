# Top scores
Write a function that takes:

- a list of unsorted_scores
- the highest_possible_score in the game

and returns a sorted list of scores in less than O(n*log n) time.

## Example
```
i/p: [3,4,3,2,4,3,5,6,7,5,6,7,1,2,8,9,9]
o/p: [1,2,2,3,3,3,4,4,5,5,6,6,7,7,8,9,9]
```

## Solution
- Hint: To get better than O(nlogn) performance use counting sort
- Another indication to use counting sort is, we're provided with the highest possible score, which can be used to created a counting array and keep track of element counts

## Code
```ruby
def top_scores(scores, max_score)
  # Count number of times a score has been seen
  scores_count = [0] * max_score

  # Count
  scores.each do |score|
    scores_count[score] += 1
  end

  sorted_scores = []

  # Print in sorted order
  scores_count.each_with_index do |count, i|
    count.times { sorted_scores << i }
  end

  sorted_scores
end
```

## Time complexity
- O(n) to count
- O(n) to construct the sorted result
- This is less than ideal since we are using up extra space for storing score counts, but if the highest_possible_score is not a very large number, then its a great trade-off to achieve O(n) sorting time.
