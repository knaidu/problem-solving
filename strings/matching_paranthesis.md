# Matching paranthesis
Write a function that, given a sentence like the one below, along with the position of an opening parenthesis, finds the corresponding closing parenthesis.

## Example
```
Input:
String - "Sometimes (when I nest them (my parentheticals) too much (like this (and this))) they get confusing."
Opening bracket index - 10

Output:
Closing bracket index - 79
```

## Solution
- Traverse the string and keep track of the number of brackets seen, for every opening bracket increment the count and for every closing bracket decrement the count
- For the closing bracket the makes the count back to 1, that means we have found the matching bracket for the input index.

## Code
```ruby
def matching_paranthesis(str, num)
  return -1 if str.nil?
  return -1 if str[num] != '('

  i = num + 1
  num_open = 1
  while i < str.size
    if str[i] == '(' # opening brace
      num_open += 1
    elsif str[i] == ')' # closing brace
      num_open -= 1
      return i if num_open == 0
    end
    i += 1
  end

  return -1
end
```

## Complexity
We're using O(1) space for counting the number of open brackets and O(n) time since we are traversing the string only once

## Variant
If we had to perform this search repeatedly, we wouldn't want to incur the O(n) cost each time. We can pre-process the string and store the opening and closing index pairs in a data structure.

- Traverse the string L to R and for every opening bracket push its index into a stack
- For every closing bracket pop from stack, and store the indices in their respective hash
    ```ruby
    # After pre-processing
    closing_bracket_index = {10 => 79}
    # { opening_index => closing_index }

    opening_bracket_index = {79 => 10}
    # { closing_ndex => closing_index }
    ```
- Now for any given index in the string, if its an '(' we can lookup its matching closing bracket hash and vice versa.
    ```ruby
    if str[i] == '('
        return closing_bracket_index.find(i)
    elsif str[i] == ')'
        return opening_bracket_index.find(i)
    end
    ```
- Complexity
    - O(n) space complexity,
    - O(1) for lookup,
    - O(n) pre-processing
