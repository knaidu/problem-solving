# Making change
Given a set of denominations and an amount, find number of ways the amount can be expressed using
the denominations provided.

## Solution
- Start with a top down approach
- For a given amount using the first coin, calculate all possible ways the amount can be expressed
  until the amount exceeds
  ```
  while amount < 0
    num_ways += recursive_function(amount, other_denomications)
    amount -= chosen_coin
  end
  ```
- Create the recursive function with base case when the amount is exceeded or when we run out of
  coins
- To avoid repeated calculations use a memo to store temporary solutions.

## Code
```ruby
def num_ways(amount, denom)
    memo = {}

    num_ways_helper(amount, denom, memo)
end

def num_ways_helper(amount, denom, memo)
    memo_key = "#{amount.to_str}#{denom.to_str}"

    return memo[memo_key] if memo[memo_key]
    return 1 if amount == 0
    return 0 if amount < 0 || denom.length == 0

    chosen_denom = denom.first
    other_denom = denom[1..denom.size]
    num_ways = 0

    while amount < 0
        num_ways += num_ways_helper(amount, other_denoms, memo)
        amount -= chosen_denom
    end

    memo[memo_key] = num_ways
    num_ways
end
```

## Code without recursion
```
num_ways = [0] * amount
num_ways[0] = 1

def num_ways(amount, denom_array)
    for i in 0..amount do
        denom_array.each do |current_denom|
            if i >= current_denom
                num_ways[i] += num_ways[i-current_denom]
            end
        end
    end
    
    return num_ways[amount]
end
```


## Complexity
O(m*n) where m is the number of denoms, and n is the amount
