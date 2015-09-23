# Longest matching parenthesis
Given a string containing parenthesis, find the length of the longest matching parenthesis

## Example
```
Input: (())()((()
Output: 6 (from index 0 to 6)
```

## Solution
- Use a stack to keep track of indices of left paren
- Parse the string
    - When char is left paren, push to stack
    - When char is right paren, pop from stack, and calculate len = i - stack.top()
    - Keep track of the max length seen so far
    
## Code
```ruby
def longest_matching_parenthesis(str)
    return nil if str.nil?
    
    i = 0
    stack = []
    max_length = 0
    while i < str.size do
        if str[i] == '('
            stack.push(i)    
        else
            stack.pop
            length = i - stack.top
            max_length = [max_length, length].max
        end
    end
    
    return max_length
end
```