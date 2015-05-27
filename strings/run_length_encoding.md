# Run length encoding
Implement run-length encoding and decoding functions. Assume the string to be encoded consists of letters of the alphabet, with no digits, and the string to be decoded is a valid encoding.

## Solution
Encoding
- Use 2 pointers to parse through the string, the left and right pointer indicates the first and last occurrence of the char to be encoded.
- Computer the number of occurrences, then update the pointers to point to the next char
    ```ruby
    def encode
        return 'INVALID INPUT' if @data.nil?

        result = ''

        i = 0
        j = i

        while i < data.length
          j += 1 if j < data.length

          if data[i] != data[j]
            result = "#{result}#{j-i}#{data[i]}"
            i = j
          end
        end

        result
    end
    ```

Decoding
- Use left and right pointer such that left points to the number of occurrence and right points to the char to be decoded
- Carefully handle cases where there can be multiple digits in the number of occurrence field
    ```ruby
    def decode(encoded_data)
        return 'Invalid encoding' if encoded_data.nil? || encoded_data.length < 2

        i = 0
        j = 1
        result = ''

        while j <= encoded_data.length
          if char?(encoded_data[j])
            result = expand(encoded_data[i...j].to_i, encoded_data[j], result)
          else
            j += 1
            next
          end

          i = j+1
          j = i+1
        end

        result
    end

    def char?(c)
        c.to_i == 0 && !("#{c.to_i}" == c)
      end

    def expand(num, c, result)
        num.times do
          result = "#{result}#{c}"
        end

        result
    end
    ```

## Time complexity
In both cases since we are traversing the string only once, its O(n)
