# Non-uniform random number
You are given numbers from t0.. tn and probabilities from p0.. pn which sum up to 1.
Given a random number generator that generates random numbers uniformly between
[0,1], how would generate a number in T which obey the specified probabilities.

## Solution
- Hint: Think of placing the probabilities along the number line and picking
  the number from T along this line.
- Create a probability sum array p0, p0+p1, p0+p1+p2 ..
```ruby
def partial_sum(p)
  i = 0
  result = []
  result << 0
  while i < p.size
    result << result.inject(:+) + p[i]
  end
end
```
- Now generate a random number and find where it lies in this probability sum array
- Use binary search to find it in O(log n)
```ruby
def search(arr, k)
  # Setup for binary search
  low = 0
  high = arr.size - 1
  mid = (low + high) / 2

  # Search for element until high and low become equal
  while low < high
    if arr[mid] == k
      return mid
    elsif arr[mid] < k
      low = mid + 1
    else
      high = mid - 1
    end

    # Return the next largest element to k from the array
    arr[mid] > k ? return mid : return mid + 1
  end
end
```
- Now index the array T and return the respective number

## Code
```ruby
def generate(t, p)
  # Create probability sum array (number line)
  probability = partial_sum(p)

  # Generate random number between [0,1]
  rand = get_random_number(0, t.size)

  # Return the matching element from t
  return t[search(probability, rand)]
end
```

## Time Complexity
O(n) to setup the probability sum array and O(log n) to search each time.


