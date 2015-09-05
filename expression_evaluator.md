# Expression evaluator
Given a mathematical expression with brackets and operators, write a program to evaluate it and return the result

## Example
```
Input: (1+2)*3-4
Output: 5
```

## Solution
- Use 2 stacks, one for numbers and the other for operators including brackets
- When a number is found push onto the number stack
- When an operator is found
    - If its higher precedence than the one on top of stack then push 
    - Else, pop the operator along with 2 numbers, evaluate the result and push onto number stack
- When a ( bracket is found
    - Push onto operator stack
- When a ) bracket is found 
    - Pop an operator, along with top 2 numbers, evaluate it and push the result onto number stack
    - If a ( is popped, just discard it
- Once the entire string is processed, repeat above steps until operator stack becomes empty
    
## Code
```ruby
def evaluate_expression(str)
    return nil unless str
    
    operator_stack = []
    number_stack = []
    
    str.each do |c|
        # Operator found
        if '+-*/'.include(c)
            operator_stack.push(c) if operator_stack.empty?
            if higher_precedence?(c, operator_stack)
                operator_stack.push(c)
            else
                evaluate
            end
        elsif
    end
end

def higher_precedence?(c, operator_stack)
    return false if '*/'.include?(operator_stack.top)
    
    true
end

```