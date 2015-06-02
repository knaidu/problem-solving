# Primitive types
Given an array_of_ints, find the highest_productyou can get from three of the integers.

## Solution
- The key here is to identify that there will be negative numbers in the array of ints, and that the highest product could result out of 2 lowest negative values as well.
- For example: 2, -100, -100 would result in 20000.
- We should therefor keep track of the highest_product_of_3, highest_product_of_2, lowest_product_of_2, highest_num and lowest_num.

## Code
```ruby
def highest_product_of_3(array)
    highest = max(array[0], array[1])
    lowest = min(array[0], array[1])

    highest_of_2 = array[0] * array[1]
    lowest_of_2 = array[0] * array[1]

    highest_product_of_3 = array[0] * array[1] * array[2]

    i = 1
    while i < arr.length
        highest = max(highest, array[i])
        lowest = min(lowest, array[i])

        highest_product_of_3 = max(
            highest_product_of_3,
            highest_of_2 * array[i],
            lowest_of_2 * array[i]
        )
    end
end
```
