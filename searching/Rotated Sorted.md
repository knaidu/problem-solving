# Rotated Sorted

Suppose you are given an array A of n sorted numbers that has been circularly shifted k positions to the right. Find an element X in it.

## Example
```
search([35,42,5,15,27,29], 27) # => 4
```

## Algorithm
- Modify binary search, the decision to search left or right sub array should now be done based on the trend of low, mid, high and where the rotation point of the array might be present
- If key > a[mid] && key < a[high]
    - Search in the right sub-array
- Else if, key > a[low] || key < a[mid]
    - Search in the left sub-array

## Code
```

```

## Test cases
```

```

## Time complexity
O(log n), since we are essentially using binary search with a little bit of modification
