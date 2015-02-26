# Num. Occurrences

Given a sorted array which contains scores that range from 0 to 100. Write a program to find occurrence of given score.

## Example

- Array  : 1,1,1,40,40,40,100,100
- Input  : 40
- Output : 3


## Algorithm
* Approach 1
    * use hash table, scan all elements, and track count of each element seen
    * then lookup form the hash table and return the result
* Approach 2
    * Since the array is sorted the hint is to use binary search
    * find the first and last occurrence of the elelemt using binary search
    * calculate the difference and return that as the result
* Approach 1 vs 2
    * Use approach 1 when there might be repeated queries
    * There is upfront cost of scanning all the elements and storing them in a hash table
    * But the gain is future queries are relatively cheap/free
    * Use approach 2 when space is a constraint, and the chances of repeated queries are pretty low.

## Code
```

```

## Test cases
```

```

## Time complexity
- Approach 1: Scanning all elements O(n) + Lookup in hash table O(1)
- Approach 2: Binary search for first occurrence O(log n) + Binary search for last occurrence O(log n) = O(log n)
