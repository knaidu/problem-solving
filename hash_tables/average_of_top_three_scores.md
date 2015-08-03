# Average of top three scores
Write a program that takes as input a file containing test scores and returns the student who
has maximum score averaged across their top three tests.

## Solution
- Read the file and maintain a hash table of student_id => top three scores
- Use a min heap to dynamically maintain top three scores for each student
- The parse over the hash and maintain the top student so far

## Code
```ruby
def top_student(file)
    hash = {}
    while !file.end
        line = file.read_next_line
        id, score = line.split(',')
        if hash[id]
            min_heap = hash[id]
            if min_heap.size == 3
                min_heap.extract_min
                min_heap.insert(score)
            else
                min_heap.insert(score)
            end
        else
            min_heap = MinHeap.new(score)
        end
    end

    top_sum_so_far = 0
    top_student_so_far = 0
    hash.each do |id, min_heap|
        sum = sum(heap)
        if sum > top_score_sum
            top_sum_so_far = sum
            top_student_so_far = id
        end
    end

    top_student_so_far
end

def sum(heap)
    sum = 0

    while !heap.empty?
        sum += heap.extract_min
    end

    sum
end
```

## Complexity
- Time: O(n) to parse over all scores in the file, O(n log 3) to maintain top 3, this can be
  treated as constant time, O(n) to determine top among all the scores
