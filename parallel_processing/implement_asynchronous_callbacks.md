# Implement asynchronous callbacks
Implement a requestor class with dispatch method which takes the request object and a process
response method and an execute method that process the request object for x amount of time.

## Solution
- Launch a thread on receiving a request, this thread also starts a timer to keep track of timeout
- Within this thread launch another inner thread that performs the actual computation
- Interrupt from the parent thread upon timeout and process the callback

## Code
```ruby
def execute(request, delay)
    begin
        str = extract_string_from(request)
        result = process(str)
        Thread.sleep(delay) # simulate indeterminate time
    rescue InterruptedException => e
        raise InterruptedError.new('Interrupted when processing str')
    end

    result
end

def dispatch(requestor, timeout)
    request = requestor.request
    outer_task = Runnable.new {
        inner_task = Runnable.new {
            def run()
                response = execute(request, rand)
                # Process call back function
                requestor.process_response(response)
            end
        }

        def run()
            begin
                inner_thread = Thread.new(inner_task)
                inner_thread.start
                Thread.sleep(timeout)
                inner_thread.interrupt
            rescue InterruptedException => e
                puts e
            end
        end
    }
    outer_thread = Thread.new(outer_task)
    outer_thread.start

end
```
