# Matrix multiplication
Given 2 square matrices, multiply them and provide the result matrix

## Formula for multiplication 
```
a b  *  e f   =  a*e+b*g a*f+b*h
c d     g h      c*e+d*g c*f+d*h
```

## Solution
- Use 3 for loops, one for row, col and for the final multiplication

## Code
```ruby
def matrix_multiplication(a, b)
    return a if b.nil?
    return b if a.nil?
    
    c = [[0]*a.size] * a.size
    for i in 0..a.size do
        for j in 0..b.size do
            sum = 0
            for k in 0..a.size o
                sum += a[i][k] * b[k][j]
            end
        end
    end
    
    c
end
```

## Complexity 
O(n^3) due to the 3 nested loops