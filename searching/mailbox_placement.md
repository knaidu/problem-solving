# Mailbox placement
There are n buildings on a street, you are given the distances of each of those buildings from the
starting of the street. Find the optimal mailbox placement such that the distance the residents
must walk to the mail box should be minimal from all the buildings. Assume all buildings have
same number of residents

## Solution
- Reduce this problem to finding the median of all the distances
- The median is the point which is closest from all the buildings
- To find the median effeciently we can use the kth largest algorithm and find the n/2th element
  in the hypothetical sorted distances array

## Variation
- If the number of residents are provided we can perform the same algorithm in a weighted fashion,
 taking into account the number of residents per building.
