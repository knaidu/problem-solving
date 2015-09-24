# Fair bonus
Given an array of lines of code written by developers, assign bonus to each of them such that, if a developer wrote more lines of code than his neighbor he must have a higher value assigned to him.

## Solution
- Assign 1 as a bonus to each developer
- Make a pass from left to right and 1 if the left neighbor is higher than current
- Make another pass from right to left and update if the right neighbor if higher than current

## Code
```ruby
def fair_bonus(arr)
  return nil if arr.nil?

  bonus = [1]*arr.size
  i = 1

  # Go from left to right and increment bonus
  while i < arr.size
    if arr[i] > arr[i-1]
      puts "index: #{i}"
      bonus[i] = bonus[i-1] + 1 # Increase bonus 1 more then left neighbor
    end
    i += 1
  end

  # Go from right to left an increment bonus
  i = arr.size - 2
  while i >= 0
    if arr[i] > arr[i+1]
      # Max of right neighbor + 1 or current bonus if its the already higher
      bonus[i] = [bonus[i], bonus[i+1] + 1].max 
    end
    i -= 1
  end

  bonus
end
```