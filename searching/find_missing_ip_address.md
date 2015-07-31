# Find missing IP address
Given a file with a billion IP addresses find the missing one.

## Solution
- Use reservoir sampling technique.
- Separate the total sample space into 2 buckets and count them based on the bits.
- Depending on which bucket has the lower count look for the missing IP on that bucket.
