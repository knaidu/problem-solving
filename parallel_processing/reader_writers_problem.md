# Reader writers problem
Given a variable that is allowed to be read parallely by multiple threads but only one thread
can write to it at any time to maintain consistency. Implement the reader-writers.

## Solution
- Use a read lock and a write lock
- Read threads can acquire read lock, increment the read count, read var and release lock
- Write threads must acquire write lock and wait until read count is 0 before acquiring read lock
  and only then update the var.

## Code
```ruby
def reader(object)
    object.read_lock.acquire do
        object.reader_count += 1
    end

    puts "Value: #{object.value}"

    object.read_lock.acquire do
        object.reader_count -= 1
        object.read_lock.notify
    end
end

def writer(object, value)
    object.write_lock.acquire do
        object.read_lock.acquire do
            while(true)
                if object.reader_count == 0
                    object.value = value
                    break
                else
                    object.read_lock.wait # wait for notify
                end
            end
        end
    end
end
```

## Variant: Implement this with writers preference
To prioritize writers over readers, force the readers to acquire a write lock in addition to read lock. This will ensure if a writer is already waiting to acquire read lock it  gets priority over other readers
