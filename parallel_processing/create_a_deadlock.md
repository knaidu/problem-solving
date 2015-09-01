# Create a deadlock

## Solution
- Create 2 threads, t1 acquires lock1 and waits to acquire lock2
- Thread t2 acquires lock2 and waits to acquire lock1

## Code
```ruby

def thread2_run()
    lock2.acquire()
    lock1.acquire()
    puts "t2 finished processing"
end

def main()
    task1 = Runnable.new {
        def run()
            lock1.acquire()
            lock2.acquire()
            puts "t1 finished processing"
        end
    }
    task2 = Runnable.new {
        def thread2_run()
            lock2.acquire()
            lock1.acquire()
            puts "t2 finished processing"
        end
    }

    t1 = Thread.new(task1)
    t2 = Thread.new(task2)
    t1.start()
    t2.start()
end
```
