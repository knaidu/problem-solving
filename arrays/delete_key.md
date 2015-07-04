# Delete key
Given a key, delete all occurrences of it from the array

## Example
```
delete_key([5,1,6,3,4,5,8,3,5], 5) #=> [1,6,3,4,8,3]
delete_key([5], 5) #=> []
```

## Solution
- Traverse the array, use a read and write index, skip over all the elements that match the key

## Code
```ruby
def delete_key(arr, key)
  read = 0
  write = 0

  while(read < arr.size)
    if(arr[read] != key)
      arr[write] = arr[read]
      write += 1
    end
    read += 1
  end

  arr[0..write-1]
end
```

## Complexity
Time: O(n), single traversal over the array
Space: Constant space


