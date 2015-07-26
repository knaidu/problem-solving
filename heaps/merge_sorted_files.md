# Merge sorted files
Given an array of sorted numbers, sort them into a single sorted array.

## Solution
- Use heap to store 1 element from each array
- Extract min and isert it into the sorted result
- Add the next element from the array to which the extracted result belonged
- Repeat this until all elements are exhausted
- This is applicable to files stored on disk, and is effecient since we're only holding
 one element per file in memory(heap) and writing the sorted result out to disk again.

## Code
```ruby
class ArrayOfArraysSorter
    # Comparator for min heap
    def comparator(element1, element2)
        element1.data < element2.data
    end

    # Sort an array of sorted arrays
    def sort(arr)
        min_heap = MinHeap.new(comparator)

        # Insert first element from each array into heap
        i = 0
        while i < arr.size
            # Min heap element contains the data and the array to which it belongs
            element = Element.new(arr[i].first, i)
            min_heap.insert(element)
            i += 1
        end

        # Pointer array to determine next element to insert
        # initialized to second element of each array
        arr_ptrs = [1]*arr.size

        # Sort
        sorted_result = []
        while !min_heap.empty?
            # Extract min and insert into result array
            element = min_heap.pop
            sorted_result << element.data
            which_array = element.index

            # Insert if there are any remaining elements in the array
            if which_array < arr_ptrs[which_array].size
                min_heap.insert(arr[arr_ptrs[which_array]], which_array)
                arr_ptrs[which_array] += 1
            end
        end

        result
    end
```

## Complexity
- Time: O(h) to insert element into heap, O(1) to extract min, total time O(h * n), where h is
  the number of sorted arrays or the number of elements in the heap = log n, therefore
  time complexity for sort is O(n * log n)
- Space: O(h) the number of files or sorted arrays provided.
