# Sample offline data
Let A be an array of n distinct elements. Design an algorithm that returns a subset of k elements of A. All subsets should be equally likely. Use as few calls to the random number generator as possible and use O(1) additional storage. You can return the result in the same array as input.

## Example
```
offline_sampling([1,2,3,4,5,6,7,8,9], 1) # => [5]
offline_sampling([1,2,3,4,5,6,7,8,9], 2) # => [3, 9]
offline_sampling([1,2,3,4,5,6,7,8,9], 3) # => [2, 4, 6]
```

## Algorithm
- Generate a random number r and move a[r] towards the end of the array
- Do this k times
- Now the result is available in the last k elements of the array

## Code
```
def offline_sampling(array, k)
  if k <= 1
    return array[rand(array.size)]
  end

  end_ptr = array.size - 1
  k.times do
    r = rand(end_ptr)
    swap(array, r, end_ptr)
    end_ptr -= 1
  end

  return array.slice(end_ptr+1, array.size-1)
end
```

## Test cases
```
offline_sampling([1,2,3,4,5,6,7,8,9], 1) # => [5]
offline_sampling([1,2,3,4,5,6,7,8,9], 2) # => [3, 9]
offline_sampling([1,2,3,4,5,6,7,8,9], 3) # => [2, 4, 6]
offline_sampling([1,2,3,4,5,6,7,8,9], 9) # => [2, 4, 6, 3, 1, 9, 8, 7, 5]
```

## Time complexity
O(k), visiting each element only 1 time and visiting only k elements
Assumption here is call to rand() is constant
