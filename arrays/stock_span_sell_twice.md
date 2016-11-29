# Stock span sell twice
Given an array of prices, you are allowed to buy and sell twice. Only requirement being you must
sell before you buy again. Find the maximum profit that can be made.

## Solution
- The key is determining when to sell the first time
- Lets use 2 phases
    - Forward phase: Calculate max profit so far if we sell on each day, going from 0 to n
    - Backward phase: Calculate max profit so far if we buy on each day, going from n to 0

## Code
```ruby
def buy_and_sell_stock_twice(arr)
  # Forward phase
  min_so_far = 999
  max_profit = 0
  first_max_profit = []
  i = 0
  while i < arr.size
    min_so_far = [min_so_far, arr[i]].min
    max_profit = [max_profit, arr[i] - min_so_far].max
    first_max_profit[i] = max_profit
    i += 1
  end

  # Backward phase
  max_so_far = 0
  total_max_profit = 0
  i = arr.size - 1
  while i >= 0
    max_so_far = [max_so_far, arr[i]].max
    total_max_profit = [total_max_profit, (max_so_far - arr[i]) + (first_max_profit[i - 1])].max
    i -= 1
  end

  total_max_profit
end
```

## Complexity
- Time: O(n) since we are traversing the array ony twice
- Space: O(n) since we are storing max profits for sale on each day in the first phase
