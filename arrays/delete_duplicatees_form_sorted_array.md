# Delete duplicates from sorted array
Given a sorted array with duplicate elements, eliminate the duplicate elements in place.

## Example
```
i/p: [1,1,1,2,3,4,4,4,5,6,7,7,7]
o/p: [1,2,3,4,5,6,7]
```

## Solution
- Use 2 pointers read and write, check for duplicates and overwrite the write pointer with the next unique element

## Code
```ruby
def eliminate_duplicates(a)

    write = 0
    read = 1

    while (read < a.size)
        if a[read] == a[read - 1]
            read += 1
        else
            a[write] = a[read-1]
            write += 1
            read += 1
        end
    end
end
```

## Complexity
O(n) time complexity, since we traverse that array only once
O(1) space complexity, since we do not use any additional space to store the elements.
