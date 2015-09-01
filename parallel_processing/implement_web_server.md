# Implement web server

## Solution
- Web server, needs a server to run on specified port
- The server should accept connections one at a time in an infinite while loop until terminated
- Once a new connection is established, it should be handed off to the worker to process in a thread
- Instead of spawning one thread at a time, use a thread pool that is more memory efficient

## Code
```ruby
def service(num_threads, server_port)
    exec = Executor.with_thread_pool(num_threads)
    server_socket = ServerSocket.new

    while(true)
        conn = server_socket.accept # blocking call
        task = Runnable.new {
            def run()
                Worker.handle_request(connection)
            end
        }
        exec.execute(task)
    end
end
```
