# Unix tail command

Implement UNIX tail command. You are given the filename and the number of lines to print from the
end of the file.

## Solution

* Unix does allow random file access, so treat it like an array and read chars from the end of
  file moving towards the start.
* When the desired number of lines are read, stop the pointer there and print from that point
  until end of file.

## Code

```ruby
def tail(filename, num_lines)
    return nil if filename.nil? or num_lines == 0

    file = File.open(filename)

    lines_read = 0
    i = 0
    # Find (end-i)th line
    while i < file.size
        c = file_ptr.read_char(file.end - i)
        lines_read += 1 if c == '\n'
        break if lines_read > num_lines
        i += 1
    end

    # Print last num_lines
    while i < file.size
        puts file_ptr.read_char(i)
        i += 1
    end
end
```

## Time complexity

* Time O\(n\), when n is the num of lines requested
* Space O\(1\), no extra space is used to store temp lines

