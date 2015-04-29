# Bracket Validator
Write a braces/brackets/parentheses validator.

## Example
```
"{ [ ] ( ) }" => true
"{ [ ( ] ) }" => false
"{ [ }"       => false
```

## Algorithm
- Use a stack and push every open brace into it
- When you encounter a closing brace pop the element from the stack and check if it matches with its opening brace
- After you parse the entire string if any elements are still left in the stack then we the string did not have valid paranthesis

## Code
```ruby
def is_valid(input)
  matchers = { '(' => ')', '{' => '}', '[' => ']' }
  openers = matchers.keys
  closers = matchers.values
  stack = []

  input.each_char do |c|
    if openers.include?(c)
      stack.push(c)
    elsif closers.include?(c)
      stack.pop == matchers[c]
    end
  end

  stack.size == 0
end
```

## Test cases
```
is_valid("(a)") => true
is_valid("( ) ( )") => true
is_valid("( ) [ ]") => true
is_valid("( [ ) ]") => false
is_valid("( [ )") => false
is_valid(") (") => false
is_valid("{ [ ( ] ) }") => false
```

## Time complexity
Since we are parsing the string only once, O(n)

