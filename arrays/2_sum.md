# 2 SUM
Given an array, find a pair in the array that would add up to the given sum.

## Example
```
find_pair(array = [1,2,3,4,5], sum = 5) => Pair: 1 and 4
```

## Algorithm
- Create a hash:
    - key: array element
    - value: num occurrence of that element
- Traverse the array, for every element check
    - If (sum - element) exits
    - ensure that its not the element itself

## Code
```ruby
def find_pair(array, sum)
  number_hash = convert_to_hash(array)
  array.each do |e|
    number_hash[e] -=1
    if pair_exists?
      puts "Pair found: #{e} and #{sum-e}"
      break
    end
    number_hash[e] +=1
  end

  puts 'Pair not found'
end

def pair_exists?(e, sum)
  number_hash.include?(sum - e) && number_hash[sum-e] > 0
end

def convert_to_hash(array)
  number_hash = {}
  array.each do |e|
    if number_hash.include?(e)
      number_hash[e] += 1
    else
      number_hash[e] = 1
    end
  end

  number_hash
end
```

## Time complexity
O(n) - to process the array into a hash
O(n) - to traverse the array to find sum-x element
O(1) - to lookup sum-x in the hash table
Overall: O(n+n) = O(n)
