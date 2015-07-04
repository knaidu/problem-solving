# Identify the celebrity
You have a room with n people. A celebrity walks in.Everyone knows the celebrity, the celebrity knows no one.
Non-celebrities may/may not know anyone in the room. Give an algorithm to find the celebrity.

## Solution
- Use the fact that the celebrity knows no one else, and everyone must know the celebrity
- Compare adjacent elements in the array and determine who among the two can be a celebrity
    - If a knows b, a cannot be celebrity, b is a probable celebrity
    - Else if b knows a, then b cannot be the celebrity, a is a probably celebrity
- Repeat above until we have examined all elements in the array

## Code
```ruby
def identify_celebrity(arr)
    i = 1
    celebrity = arr[0]
    while (i < arr.size)
        celebrity = arr[i] if knows(celebrity, arr[i])
        i += 1
    end

    celebrity
end

def knows(a, b)
    // Returns true if a knows b, else false
end
```

## Complexity
O(n) to traverse the array once.
