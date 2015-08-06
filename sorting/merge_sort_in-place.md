# Merge sort in-place
Write a program that takes as input two sorted arrays of integers, and updates the first array to
have combined entries of the two arrays in sorted order. Assume the first array has enough empty
spaces in the end to hold all the elements.

## Example
```
Input:
arr1 - [1,3,5,nil,nil,nil]
arr2 - [2,4,6]

Output:
arr1 - [1, 2, 3, 4, 5, 6]
```

## Solution
- Use 2 pointers for each array to compare the elements
- Use a third pointer for insertion of the result
- Do this in reverse order, i.e. from the end of the array since there is extra space there
  and we wont have to move the elements around

## Code
```ruby
def merge_sort_inplace(arr1, arr2)
  # Assume arr1 has extra space at the end to accommodate arr1+arr2 elements
  # Assume arr1 and arr2 are already sorted

  return arr2 if arr1.nil?
  return arr1 if arr2.nil?

  # Insertion pointer
  k = arr1.size - 1

  # Pointer i and j point to the right most element from both arrays
  i = k
  while arr1[i].nil?
    i -= 1
  end
  j = arr2.size - 1

  # Merge and insert at the end of arr1
  while i >= 0 && j >= 0
    if arr1[i] > arr2[j]
      arr1[k] = arr1[i]
      k -= 1
      i -= 1
    else
      arr1[k] = arr2[j]
      k -= 1
      j -= 1
    end
  end

  while i >= 0
    arr1[k] = arr1[i]
    k -= 1
    i -= 1
  end

  while j >= 0
    arr1[k] = arr2[j]
    k -= 1
    j -= 1
  end

  arr1
end
```

## Complexity
- Time: O(n) since we're making only one pass over both the arrays
- Space: constant, since we're only using pointers and the sorting is done in-place
