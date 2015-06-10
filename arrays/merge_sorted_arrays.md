# Merge sorted arrays
Given 2 arrays that contain numbers that are already in sorted order, merge them into a single sorted array in O(n) time. Assume there is enough space at the end of first array to accommodate the result array.

## Example
```
i/p:
 [3,4,6,10,11,15,nil,nil,nil,nil,nil,nil]
 [1,5,8,12,14,19]

o/p:
 [1,3,4,5,6,8,10,11,12,14,15,19]
```

## Solution
- Hint: Since there is additional space towards the end of the array begin the comparison and merge from the end of the arrays
- Find the larger element from the tail of the arrays and proceed towards the start of the array
- Make sure you handle the case with disproportionte array sizes after the merge

## Code

```ruby

def sorted_merge(a1, a2)
  return a2 if a1.nil?
  return a1 if a2.nil?

  # find last element in a1
  i = a1.size
  while a1[i].nil?
    i -= 1
  end

  # last element in a2
  j = a2.size - 1

  # last element of sorted array
  k = a1.size - 1

  while i>=0 && j>=0
    puts "a1[i]: #{a1[i]}, a2[j]: #{a2[j]}"
    if a1[i] > a2[j]
      a1[k] = a1[i]
      i -= 1
    else
      a1[k] = a2[j]
      j -= 1
    end
    k -= 1
  end

  # Elements left in a1
  while i > 0
    a1[k] = a 1[i]
    i -= 1
    k -= 1
  end

  # Elements left in a2
  while j > 0
    a1[k] = a2[j]
    j -= 1
    k -= 1
  end

  a1
end
```

## Complexity
- O(n) since we are traversing over both arrays only once
