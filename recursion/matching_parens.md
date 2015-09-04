# Matching parens
Given a value n, generate all combinations of matching parens.

## Example
```
n = 1 => ['()']
n = 2 => ['()()', '(())']
n = 3 => ['()()()', '(())()', '()(())', '(()())', '((()))']
```

## Solution
- Use recursion and figure out the base case first, i.e. for 1 pair return '()'
- For 2, use the result of 1 and then concatenate '()' at the start and end (keeping result unique)
- Also, add ( and ) as leading and trailing ) to all results from n = 1
- Repeat for n = 3 and so on.

## Code
```ruby
def matching_parens(n)
    return [] if n == 0

    return ['()'] if n == 1

    # Use a set to make sure the results are unique when adding () to both ends
    result_set = Set.new

    # Recurse for n-1
    result = matching_parens(n-1)

    result.each do |r|
        # Add () to both ends
        result_set.add("#{r}()")
        result_set.add("()#{r}")

        # Add ( and ) around the result
        result_set.add("(#{r})")
    end

    result_set.to_array
end
```

## Complexity
- (2k)!/ (k!(k+1)!)
