# Locking in a tree
A binary tree node can be locked or unlocked only if none of its parents or children are locked.
Assume each node has parent pointer. Write the following methods -
- to test if a node is locked
- to lock a given node, should return if we were able to lock else false
- to unloack a given node,

## Solution
- For each node keep track of the number of nodes in its subtree that are locked
- To lock,
    - check child locked count
    - check all nodes in the path to parent
    - if none of the above are locked, then mark node as locked
- To unlock
    - mark node as unlocked
    - update all nodes in the path to parent and decrement their lock count

## Code
```ruby
class BinaryTreeNode
    attr_accessor :is_locked, :lock_count, :parent

    def is_locked?
        return @is_locked
    end

    def lock
        return false if @lock_count != 0

        # Check all nodes on path to parents if they are locked
        iter = @parent
        while iter
            return false if iter.is_locked?
            iter = iter-> parent
        end

        @is_locked = true

        # Update lock count for all nodes on path to parent
        iter = @parent
        while iter
            iter.lock_count += 1
            iter = iter.parent
        end

        return true
    end

    def unlock
        return if is_locked == false

        @is_locked = false

        # Update all nodes on path to parent
        iter = @parent
        while iter
            iter.lock_count -= 1
            iter = iter.parent
        end
    end

end
```
