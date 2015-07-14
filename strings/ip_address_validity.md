# IP address validity
Given a string that represents possible IP addresses, they are missing the ".". Evaluate and
generate all possible valid IP addresses from the string.

## Example
```
ip: '19216811'
op: '192.168.1.1', '19.216.81.1', ..
```

## Solution
- Insert the 3 dots at all possible locations and verify if the resulting IP address is valid

## Code
```ruby
# Generate all possible IP addresses from given string
def print_valid_ip_address(ip_string)
  return nil if ip_string.nil

  (1...4).each do |i|
    first = ip_string[0...i]
    return false unless valid_ip?(first)

    (i...i+3).each do |j|
      second = ip_string[i...j]
      return false unless valid_ip?(second)

      (j...j+3).each do |k|
        third = ip_string[j...k]
        fourth = ip_string[k...-1]
        return false unless valid_ip(third) && valid_ip(fourth)

        ## Validated successfully
        puts "#{first}.#{second}.#{third}.#{fourth}"
      end
    end
  end
end

# Verify a valid IP address
def valid_ip(str)
  return false if str == '00' || str == '000'
  return false if str.to_i > 255

  return true
end
```

## Complexity
- There are 2^32 possible IP addresses, therefore this algorithm which generates as many
  possible IP addresses is constant.
