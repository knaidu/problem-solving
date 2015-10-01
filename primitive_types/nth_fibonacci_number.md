# Nth Fibonacci number
Write a function fib() that a takes an integer n and returns the nth Fibonacci number.

## Example
```
fibo(5) => 5
fibo(10) => 55
```

## Solution
- We can use a top down recursive approach and memoize it to make it efficient, but we're adding
  extra O(n) space here.
- Or we can use a bottom up iterative approach and avoid using the extra space

## Recursive Code
```ruby
def fibo_helper(n, fibo_hash)
  return n if n == 0 || n == 1

  return fibo_hash[n] if fibo_hash[n]

  fibo_hash[n-1] = fibo_helper(n-1, fibo_hash)
  fibo_hash[n-2] = fibo_helper(n-2, fibo_hash)

  return fibo_hash[n-1] + fibo_hash[n-2]
end

def fibo_recursive(n)
  fibo_hash = {}

  fibo_helper(n, fibo_hash)
end
```

## Iterative code
```ruby
def fibo_iterative(n)
  return n if n == 0 || n == 1

  i = 2
  current = 1
  prev = 0

  while i <= n
    fib = current + prev
    prev = current
    current = fib
    i += 1
  end

  fib
end
```

## Complexity
- O(n) time and O(1) space using the iterative approach
- O(n) time and O(n) space using the memoized recursive approach
