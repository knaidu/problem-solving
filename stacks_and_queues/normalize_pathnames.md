# Normalize pathnames
Give a path name (absolute or relative) normalize it and return the shortest path representing the given path.

## Example
```
normalize('/abc/def/../') #=> 'abc/'
normalize('/abc/def/../../') #=> ''
normalize('abc/def/../../../') #=> '../'
normalize('/abc/def/../../../') #=> Invalid path name
```

## Solution
- Use a stack to keep track of the path name
- Split the pathname by '/'
- Push into the stack when we see anything other than '.' and '..'
- For '..' pop from stack
- When starting with '/' handle empty array appropriately when pop fails
- When not starting with '/' keep track of '../' seen so we can still report the shortest path

## Code
```ruby
def normalize(pathname)
  return nil if pathname.nil?

  stack = []
  i = 0
  starts_at_root = false

  # If it starts with '/' insert that into stack
  if pathname[0] == '/'
    stack.push('/')
    starts_at_root = true
    i += 1
  end

  # Split and analyze the pathname
  pathname_arr = pathname.split('/')
  while i < pathname_arr.size
    c = pathname_arr[i]

    if c == '.' || c == ''
      # Do nothing
    elsif c == ".."
      if starts_at_root && stack.empty?
        raise StandardError.new('Invalid path provided')
      elsif stack.empty? || stack.last == '..'
        stack.push('..')
      else
        stack.pop
      end
    else

      stack.push(c)
    end
    i += 1
  end

  ## Construct pathname in reverse order
  normalized_pathname = ''

  while !stack.empty?
    normalized_pathname = "#{stack.pop}/#{normalized_pathname}"
  end

  normalized_pathname
end
```

## Time complexity
- O(n) time where n is the length of the path
