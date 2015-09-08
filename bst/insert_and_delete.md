# Insert and delete
Given a bst, perform insertion and deletion on it.

## Insertion
- Do a find on the bst for the node to be inserted, eventually fall off the tree
- Keep track of the previous node, and insert the new node based on BST property

## Deletion
- Find the node to be deleted (unless you already have a pointer to the node to be deleted)
- Find the successor to this node (left most node in the right child)
- Update the node with successor value and delete the successor node
