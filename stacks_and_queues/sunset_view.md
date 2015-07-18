# Sunset view
Given a set of buildings in an array, process the buildings from east to west and return the list of buildings that have a sunset view. If a building is shorter than another building to its west then it looses its sunset view.

## Solution
- Use a stack and push elements into the stack appropriately
- If top of stack is greater than current element then push
- Else pop out of stack until the stack is empty or the top is greater than current element
- This eliminates all the buildings that do not have the sunset view

## Code
```ruby
def sunset_view(buildings)
    return nil if buildings.nil?

    s = []
    i = buildings.size -1
    while i >= 0
        insert(building[i], s)
        i -= 1
    end
end

def insert(element, s)
    if s.empty? || s.top > element
        s.push(element)
    else
        s.pop
        insert(element, s)
    end
end

```
