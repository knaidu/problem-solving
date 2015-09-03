# Tower of hanoi
Write a program that prints a sequence of steps to move a set of rings from one peg to another,
using a temporary peg. It must obey the rule that at any point a peg cannot hold a ring larger than t
the topmost ring.

## Solution
- Concept:
    - Recursively move all rings except last one from source to temp using destination as temp
    - Move the last ring to destination peg
    - Recursively move all rings from temp to destination using source peg as temp

## Code
```ruby
def compute_tower_of_hanoi(num_rings)
    pegs = [[], [], []]
    num_rings.each do |num|
        pegs[0].push(num)
    end

    tower_of_hanoi(num_rings, pegs, 0, 1, 2)
end

def tower_of_hanoi(num_rings, pegs, source_peg, temp_peg, dest_peg)
    return nil if num_rings == 0

    # Recursively move all rings except last one from source to temp using destination as temp
    tower_of_hanoi(num_rings-1, source_peg, dest_peg, temp_peg)

    # Move the last ring to destination peg
    ring = pegs[source_peg].pop
    pegs[dest_peg].push(ring)
    puts "Move #{ring} from peg:#{source_peg} to peg:#{dest_peg}"

    # Recursively move all rings from temp to destination using source peg as temp
    tower_of_hanoi(num_rings-1, temp_peg, source_peg, dest_peg)
end
```

## Complexity
- Time: 2^n
- To derive it, unrap the iterations, 1 + 2 + 4 + 8 .. leads to 2^n operations
