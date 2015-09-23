# Attacking rooks
Given a ches board represented as a matrix, rooks are placed and encoded as 0 in the matrix all other cells hold the value 1. Identify all the attacking positions for the rooks given and mark them 0. That is if there is a 0 in a particular cell mark the entire row and entire column 0.

## Solution
- Use 2 auxillary arrays one for row and other for column to keep track of where we have seen 0s.
- Once we have processed the entire matrix, and noted all the 0s, pass over the matrix again and mark the respective row and column 0.
- To optimize on space, reuse the first row and first column instead of the auxillary arrays described above, in addition use 2 variables to keep track if the first row and first column had 0s before using it for processing