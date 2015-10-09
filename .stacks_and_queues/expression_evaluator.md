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
class ExpressionEvaluator
    attr_accessors :operator_stack, :number_stack
    
    def initialize()
        @operator_stack = []
        @number_stack = []
    end

def evaluate_expression(str)
    return nil unless str
    
    operator_stack = []
    number_stack = []
    
    i = 0
    while i < str.size
        c = str[i]
        
        # Operator        
        if '+-*/'.include(c)
            @operator_stack.push(c) if operator_stack.empty?
            if higher_precedence?(c)
                @operator_stack.push(c)
                i += 1
            else
                evaluate
            end
        
        # Opening bracket
        elsif c == '('
            @operator_stack.push(c)
            i += 1
        
        # Closing bracket
        elsif c == ')'
            evaluate
            i += 1
        
        # Number
        elsif '1234567890'.include?(c)
            @number_stack.push(c)
            i += 1
        end
    end
    
    while !@operator_stack.empty? do
        evaluate
    end
    
end

def higher_precedence?(c)
    return false if '*/'.include?(@operator_stack.top)
    
    true
end

def evaluate
    # pop from operator stack
    op = @operator_stack.pop
    while op == '('
        op = @operator_stack.pop
    end
    
    # pop numbers from stack 
    # re-order the numbers when evaluating
    num1 = @number_stack.pop
    num2 = @number_stack.pop
    
    if op == '*'
        result = num2 * num1
    elsif op == '/'
        result = num2/num1
    elsif op == '+'
        result = num2 + num1
    elsif op == '-'
        result = num2 - num1
    end
    
    @number_stack.push(result)
end
```

## Compelxity
- Time: O(n) since we are parsing through the string only once
- Space: O(n) for the number + operator stack
