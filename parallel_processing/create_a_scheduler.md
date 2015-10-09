# Create a scheduler
Create a scheduler that manages execution of deferred tasks. It takes as input a runnable object,
a string as the name of the task. It must support
- Starting a thread identified by name based on  a future time provided
- Canceling a thread based on its name

## Solution
- Use a min heap to keep track of objects, keys being the time
- Use a dispatch thread to monitor if he top of heap is ready for execution
- This thread sleeps for a time between now and time at the top of heap
- When woken up, it extracts the top of heap, checks if its valid or cancelled (use a hash for state)
- It processes the object, then removes from queue
- When a new object is inserted check if the new object landed at top of heap,
  if it did then interrupt the dispatch thread and adjust its sleep time accordingly
