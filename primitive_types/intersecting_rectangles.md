# Intersecting rectangles
Given 2 rectangles, check if they intersect. Assume that both the rectangles are aligned parallel to the axis

## Solution
- If both x-axis and y-axis overlap then both the rectangles overlap

## Code
```ruby
class Rectangle
    attr_accessor x,y,width,length

    def initialize(x,y,width, length)
        @x = x
        @y = y
        @length = length
        @width = width
    end
end

def overlap?(p1, length, p2, length)
    # Find leftmost/ line among the two
    low = min(p1,p2)

    # Find rightmost/higher line among the two
    high = max(p1,p2)

    # Check if they overlap
    if low < high && low + length > high
        return true
    else
        return false
    end
end

def rectangles_intersect?(r, s)
    if overlap(r.x, r.length, s.x, s.length) &&
        overlap(r.y, r.width, s.y, s.width)
        return true
    else
        false
    end
end
```

## Complexity
O(1) since we are making finite number of comparisons to determine if the rectangles overlap
