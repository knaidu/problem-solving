# Online sampling or Reservior sampling
Given a stream of input numbers, design an algorithm that reads an integer at a time and
maintains a random sampling of k integers.

## Solution
- First read k integers from the stream
- When k+1th element is read generate random integer in the range 0..k+1
- If rand is less than k, then swap out the arr[rand]
- Else continue to the next integer in the stream

## Code
```ruby
def online_sampling(num_stream, k)
    random_sampling = []

    # Insert first k integers into the sample set
    i = 0
    while i < k
        random_sampling << arr[i]
        i += 1
    end

    # Read next integer from stream and decide if it goes
    # into the sample or not

    num_elements_read = k

    while num_elements_read < num_stream.size
        num = num_stream[num_elements_read]
        rand = random(0, num_elements_read)
        if rand < k
            sampling[rand] = num
        end

        num_elements_read += 1
    end

    return sampling
end
```

## Complexity
O(n) time where n is the total number of elements in the stream.
Assuming generating random integer takes constant time
