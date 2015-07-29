# Find square root
Given an integer find its square root

## Solution
- Use binary search to find the square root
- Search in the space 0..n and move closer to the final result in each iteration

## Code
``ruby
def square_root(num)
    return nil if num.nil?
    return num if num == 0

    low = 0
    high = num
    while low <= high
        mid = (low + high)/2
        square = mid * mid
        if square == num
            return mid
        elsif square < num
            low = mid + 1
        else
            high = mid -1
        end
    end
end
```

## Complexity
- Time: O(log n) since we're dividng the search space by half in each iteration
- Space: constance space.
