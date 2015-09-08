# Add credits
Design a data structure that can handle the following operations
- Insert: add a client with specified credit, replacing any existing entry for the client
- Remove: delete the specified client
- Lookup: return the number of credits associated with the specified client
- Add-to-all: increment the credit count for all current clients
- Max: return a client with the highest number of credits

## Solution
- A hash can be used for storing (client_id, credit) pair, which will support insert, remove and lookup in O(1), unfortunately finding max will be O(n)
- Use a BST + hash combo. Hash will store (client_id, pointer_to_bst_node)
- Bst nodes use the credit as key, so that finding max would be O(log n)
- Increment, remove and lookup will still be O(1)
- Global increments can be done by using an extra variable that should be added to the current credit in each of the bst nodes to return the current credit value
- When new nodes are added, subtract this global credit count form it and then add to BST
