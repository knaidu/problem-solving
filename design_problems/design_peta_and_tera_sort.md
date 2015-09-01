# Design peta and tera sort
How would you sort a trillion 1000 byte strings that would not fit into memory or a single
machine's disk

## Solution
### Use disk
- If it would fit into memory then a simple sort would take care of sorting them
- Since its large, we can use the disk as temp store
- Sort the input into sets of sorted output and write them to disk
- Finally merge these sorted sets to get the final sorted output

## Distributed solution
- Use multiple machines, use a distributed hash ring that would assign a piece of data to a
  specific machine. Then each machine can sort all its data (or index it in a hash).
- When searching, redirect the request based on the hashed value to the right machine,
  followed by binary search on that machine (or hash lookup)
