# Total ordering
Given 3 nodes, first, middle and last check if they are totally ordered, i.e. if middle is a descendant of first and last is a descendant of middle

## Solution
- Use interleaved searching
- Look for first or last from middle, stopping when either is found and then searching only for the other
- For example if first = A, last = J and middle = I, search for I from both A and J, stopping as soon as we get I from A and preventing an unsuccessful search from J, of course we have to complete the search for I from J to complete the computation.