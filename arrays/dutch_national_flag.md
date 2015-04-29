# Dutch National Flag

Write a function that takes an array A of length n and an index i into A, and rearranges the elements such that all elements less than A[i] appear first, followed by elements equal to A[i], followed by elements greater than A[i]. Your algorithm should have O(1) space complexity and O(n) time complexity.

## Example
```
Array  => [0, 1, 2, 0, 1, 2, 0, 1, 2, 0, 1, 2], Pivot  => 4
Result => [0, 0, 0, 0, 1, 1, 1, 1, 2, 2, 2, 2]
```

## Algorithm
1. Use a smaller pointer starting at index 0 to move elements lesser than pivot
2. Use a larger pointer to starting at last element of array, to move elementslarger than pivot
3. And middle section will have elements equal to the pivot

## Code
```ruby
def swap(x, y, a)
  temp = a[x]
  a[x] = a[y]
  a[y] = temp
end

def dnf(a, i)
  pivot = a[i]
  smaller = 0
  equal = 0
  larger = a.length - 1

  while(equal <= larger) do
    if a[equal] < pivot
      swap(equal, smaller, a)
      smaller += 1
      equal += 1
    elsif a[equal] == pivot
      equal += 1
    else # a[equal] > pivot
      swap(equal, larger, a)
      larger -= 1
    end
  end

  a
end
```

## Test Cases
```
Array in reverse order:
dnf([9,8,7,6,5,4,3,2,1], 4) => [1,2,3,4,5,6,7,8,9]

Array with only 3 types of elements:
dnf([0,1,2,0,1,2,0,1,2,0,1,2], 4) => [0,0,0,0,1,1,1,1,2,2,2,2]
```

## Time complexity
O(n), since we loop over all the elements only once.
