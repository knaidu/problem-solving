# Product array
Write a function get_products_of_all_ints_except_at_index() that takes an array of integers and returns an array of the products.

## Example
```
input: [1,7,3,4]
output: [84, 12, 28, 21]
```

## Solution
- Concept to use is maintaining product_so_far when traversing from left to right and right to left, optimizing for space and computing the result as follows:
- Step 1: Calculate product so far when traversing L to R
    ```ruby
    result = [1] * (array.size) # initialize to 1

    product = 1
    i = 0

    while i < array.size
        result[i] = product
        product = product * array[i]
        i += 1
    end
    ```
- Step 2: Calculate product so far traversing right to left and calculate the final product array using the product_so_far from the previous step
    ```ruby
    product = 1
    i = array.size - 1

    while i >= 0
        result[i] = result[i] * product
        product = product * array[i]
        i -= 1
    end
    ```

## Complexity
- Time: O(n) since we are traversing the array twice
- Space: O(n) additional space for the result array, instead of O(n) * 3 if we use 3 arrays for storing intermediate products.

