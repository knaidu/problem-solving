# Array Flattening

Write a function that flattens an Array of Array objects into a flat Array. Your function must only do one level of flattening.

## Example
```
flatten [1,2,3] # => [1,2,3]
flatten [[1,2,3],["a","b","c"],[1,2,3]]  # => [1,2,3,"a","b","c",1,2,3]
flatten [[[1,2,3]]] # => [[1,2,3]]
```

## Algorithm
1. Iterate over the array
2. Check if an element is a value or an array
3. If its an array, flatten it and insert into result array
4. If its a value, directly insert it into the result array


## Code
Ruby magic
```
def flatten(array)
  array.flatten 1
end
```

Detailed implementation
```
def flatten(array)
  result = []

  array.each do |x|
    if x.is_a? Array
      result.concat(x)
    else
      result << x
    end
  end

  return result
end
```


## Test Cases
```
Test.expect flatten([]) == []
Test.expect flatten([1,2,3]) == [1,2,3]
Test.expect flatten([[1,2,3],["a","b","c"],[1,2,3]]) == [1,2,3,"a","b","c",1,2,3]
Test.expect flatten([[3,4,5],[[9,9,9]],["a,b,c"]]) == [3,4,5,[9,9,9],"a,b,c"]
Test.expect flatten([[[3],[4],[5]],[9],[9],[8],[[1,2,3]]]) == [[3],[4],[5],9,9,8,[1,2,3]]
```

## Time complexity
- O(n), since we are visiting every element of the array only once
