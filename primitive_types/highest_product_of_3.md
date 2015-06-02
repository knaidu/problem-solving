# Highest product of 3
Given an array_of_ints, find the highest_productyou can get from three of the integers.

## Solution
- The key here is knowing that we'll have to deal with negative numbers and that the highest product of 3 could be a result of 2 low negative numbers.
- Maintain the following values as we traverse the array
    - highest_product_of_3
    - highet_product_of_2
    - lowest_product_of_2
    - highest_number
    - lowest_number

## Code
```ruby
def highest_product_of_3(array)
    highest_number = max(array[0], array[1])
    lowest_number = min(array[0], array[1])

    highest_product_of_2 = array[0]* array[1]
    lowest_product_of_2 = array[0]* array[1]

    highest_product_of_3 = array[0]* array[1] * array[2]

    i = 2
    while i < array.length
        highest_product_of_3 = max(
            highest_product_of_2 * array[i],
            lowest_product_of_2 * array[i],
            highest_product_of_3
        )

        lowest_product_of_2 = min(
            lowest_number * array[i],
            lowest_product_of_2
        )

        highest_product_of_2 = max(
            highest_number * array[i]
            highest_product_of_2
        )

        highest_number = max(
            highest_number, array[i]
        )

        lowest_number = min(
            lowest_number, array[i]
        )
    end

    return highest_product_of_3
end
```

## Time complexity
O(n) since we are parsing the array only once and using O(1) space
