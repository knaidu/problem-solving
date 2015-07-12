# Pascals triangle
Enumerate pascal's triangle

## Example
```
    1
   1 1
  1 2 1
 1 3 3 1
1 4 6 4 1
```

## Solution
- Use the result from previous result to calculate the next result

## Code

```ruby
def pascals_triangle(num_rows)
  result = []
  result << [1]

  (1...num_rows).each do |i|
    curr_row = []
    (1...i).each do |j|
      sum = result[i-1][j-1] + result[i-1][j]
      curr_row << sum
    end
    result << curr_row
  end
end
```
