# Random number generator
Given a range (a,b) generate a uniform random number in that range. You are provided a fair coin
that produces 0 or 1 with equal probability.

## Solution
- Use the fair coin to produce bits of the random number
- This will give us a number in the range 0..2^n
- If that is outside the specified range then repeat above step until.

## Code
```ruby
# Returns 0 or 1 with equal probability
def coin_toss
end

# Generate random number
def random_number
    t = b - a + 1
    num = 0
    i = 0
    while i < t
        num *= 2
        num |= coin_toss
        i = i << 1
    end

    if num > t
        return random_number
    else
        return num
    end
end
```

## Time complexity
Assuming coin_toss takes constant time, overall complexity is O(log t), where t = b - a + 1
