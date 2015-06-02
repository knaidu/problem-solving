# Interconvert string to int
Given an integer convert it to a string. Given a string convert it into its integer representation.

## Solution

### String to int
- The trick here is to operate in the ASCII values of the chars
- Parse through the string
    - convert each char into its ascii number,
    - verify it is valid
    - subtract it from the ascii value of 0 to get the numerical value of that char
    - handle the negative case appropriately


```ruby
    def int_to_string(num)
        return '0' if num == 0

        if num < 0
            is_negative = true
            num = -num
        end

        str = ''

        while num != 0
            digit = num % 10
            num = num / 10
            str = "#{digit}#{str}"
        end

        is_negative ? "-#{str}" : str
    end
```

### Int to string
- Trick here is to extract one digit at a time from the integer in right to left order starting with the LSB moving towards MSB
- Parse through each digit
    - convert it to char and append to existing chars
    - handle the negative case appropriately

```ruby
def int_to_string(num)
  return '0' if num == 0

  if num < 0
    is_negative = true
    num = -num
  end

  str = ''

  while num != 0
    digit = num % 10
    num = num / 10
    str = "#{digit}#{str}"
  end

  is_negative ? "-#{str}" : str
end
```
