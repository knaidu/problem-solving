# Phone number mnemonic
Write a function which takes as input a phone number, specified as a string of digits, return all possible character sequences that correspond to the phone number. The cell phone keypad is specified by a mapping M that takes a digit and returns the corresponding set of characters. The character sequences do not have to be legal words or phrases.

## Example
```
PhoneMnemonic.new('23') #=> AD, AE, AF, BD, BE, BF ..
```

## Algorithm
Use backtracking
- Start with the last phone number
- Append all its chars into an array
- Move to the next phone number and compute all combinations of the current number and all chars previously in the array
- Repeat this until we reach the first digit

## Code
```ruby
class PhoneMnemonic
  def initialize(phone_number)
    cell_phone_mapping = {
        '2' => 'ABC',
        '3' => 'DEF',
        '4' => 'GHI',
        '5' => 'JKL',
        '6' => 'MNO',
        '7' => 'PQRS',
        '8' => 'TUV',
        '9' => 'WXYZ',
        '0' => '',
        '1' => ''
    }

    puts generate_char_sequences(cell_phone_mapping, phone_number)
  end

  def generate_char_sequences(cell_phone_mapping, phone_number)
    result_array = initialize_result_array(cell_phone_mapping[phone_number[phone_number.size - 1]])

    i = phone_number.size - 2
    while (i >= 0)
      next_result_array = combine_char_with_result_array(cell_phone_mapping[phone_number[i]], result_array)
      result_array = next_result_array
      next_result_array = []
      i -= 1
    end

    result_array
  end

  # Initialize result set with all values from the last number
  def initialize_result_array(letters)
    result_array = []
    letters.each_char do |c|
      result_array << c
    end

    result_array
  end

  def combine_char_with_result_array(letters, result_array)
    next_result_array = []
    letters.each_char do |c|
      result_array.each do |r|
        next_result_array << c + r
      end
    end

    next_result_array
  end
end
```

## Time complexity
Since there are no more than 4 possible characters for each digit, the number of recursive calls T(n) satisfies T(n) ≤ 4T(n − 1), which solves to T(n) = O(4^n). For the function calls that entail recursion, the time spent within the function, not including the recursive calls, is O(1). For the base case, printing a sequence of length n takes time O(n). Therefore, the time complexity is O(4^n * n).
