# LRU cache
Implement a LRU cache for looking up values by key. You should support lookup, insert and delete.
Use the LRU strategy for cache eviction.

## Solution
- Use a combination of hash table and a linked list
- Insert when not full
    - Add key to hash,
    - Create a linked list node with value,
    - Insert node at the start of the linked list
    - Add a reference to this node in the hash
-Insert when full
    - Find the last node in the list, which was not recently used
    - Delete its hash key, and delete that node from the list as well
- Lookup
    - Find key in hash table, lookup its linked list node and return value
    - Move the node to the start of the list, indicating it was recently used
- Delete
    - Find the node in hash table,
    - Delete its corresponding linked list node and its key from hash

## Code
```ruby
    class LRUCache
        attr_accessors :hash, :list, :size, :max_size

        def initialize(max_size)
            @hash = {}
            @list = LinkedList.new
            @max_size = max_size
        end

        def full?
            @size == @max_size
        end

        def insert(key, value)
            node = LinkedListNode.new(key,value)
            unless full?
                @list.insert_at_beginning(node)
                @hash[key] = node
            else
                # Delete node from end of list
                @hash[@list.last.key].remove
                @list.last.delete
                @list.insert_at_beginning(node)
                @hash[key] = node
            end
        end

        def lookup(key)
            node = @hash[key]

            # move to front of list
            @list.move_to_front(node)

            node.value
        end

        def delete(key)
            node = @hash[key]

            # delete from list and hash
            @list.delete(node)
            @hash[key].remove
        end
    end
```

## Complexity
- Time: Lookup O(1), Insert (1), Delte (1)
- Space: 2n, where n is the number of keys

## LRU cache with TTL
- For each node add an adidtional field "expiry", which is the creation time + ttl
- On lookup check if the node has expired by comparing current_time with expiry
- If it has expired delete the node and return not_found
- If its has not expired, then return the value found.

