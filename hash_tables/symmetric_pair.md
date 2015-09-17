# Symmetric Pair
Given a list of pairs of the form (x,y), return a list of all the pairs that have symmetric pairs for it of the form (y,x)

## Solution
- Run through the list of all pairs and put them in the hash x => y
- Now run through the list again checking for y, if it exists in the hash then push the pair into result else continue to the next pair