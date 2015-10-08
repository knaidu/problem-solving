# K most frequent strings
You are given an array if non-distinct strings. Find the k most frequently occurring strings.

## Solution
- Use a hash table to count the frequencies of each of the strings
- Now, scan through the hash table, process it through a min heap of size k
- After processing the hash table, k most frequent elements remain in the heap
- The complexity of this approach O(n) to count, O(n log k) to find k largest frequencies
- This can be improved by applying the pivot and partition technique reducing the time
  complexity to O(n + m)

## Code
```ruby
def k_most_frequent(arr, k)
    return nil if arr.nil?
    return nil if k.nil || k <= 0

    frequency_hash = count_frequencies(arr)

    find_k_largest(frequency_hash, k)
end

def count_frequencies(arr)
    hash = {}
    arr.each do |str|
        if hash[str]
            hash[str] += 1
        else
            hash[str] = 1
        end
    end

    hash
end

def find_k_largest(hash, k)
    min_heap = MinHeap.new(comparator_function)
    hash.each do |str, count|
        if min_heap.size < k
            min_heap.insert({str: count})
        else
            min_heap.extract_min
            min_heap.insert(str: count)
        end
    end

    min_heap.to_array
end

def comparator_function(element1, element2)
    element1[str] < element2[str]
end
```
