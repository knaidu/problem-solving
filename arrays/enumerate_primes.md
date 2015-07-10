# Enumerate primes
Given an integer n, enumerate all primes upto n.

## Example
```
n = 10
primes = [2,3,5,7]
```

## Solution
- Use the seive technique
- Start from 2 to n, remove all multiples of 2 in the potential primes list
- Repeat this jumping to the next prime number until we have reached n
- There are some improvements to be made here, by skipping over any non prime number and starting
  from i^i since k*i will get eliminated anyway.

## Code
```ruby
def enumerate_primes(n)
  primes = []
  is_prime = [1] * (n + 1)
  i = 2

  while i <= n
    if is_prime[i] == 1
      primes << i
      j = i

      while j <= n
        is_prime[j] = 0
        j = j + i
      end
    end
    i += 1
  end

  primes
end
```

## Time complexity
- O(n log log n)
