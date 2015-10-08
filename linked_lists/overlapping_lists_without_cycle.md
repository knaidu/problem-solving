# Overlapping lists without cycle

Let hI and h2 be the heads of lists Ll and L2, respectively. Assume that L1 and L2 are well-formed, that is each consists of a finite sequence of nodes. (In particular, neither list has a cycle.)

How would you determine if there exists a node r reachable from both hI and h2 by following the next fields? If such a node exists, find the node that appears earliest when traversing the lists.

You are constrained to use no more than constant additional storage.

## Solution
Find length of the first list
- While traversing keep a counter and increment it untilwe reach the last node

  ```ruby
  while first.next != nil
    count += 1
    first = first.next
  end
  ```

Repeat the same for the second list
- Once we reach the last node if its same as the last node of the first list then the 2 lists are overlapping

  ```ruby
  if ptr1 != ptr2
    puts "Lists are non-overlapping"
    return nil
  end
  ```


Now determine the overlapping node
- For the list with longer length increment the head pointer by the difference in length,

  ```ruby
  ptr1 = head1
  ptr2 = head2

  if count1 > count 2 // find the longer list
    diff = count1 - count2
    while diff != 0
        ptr1 = ptr1.next
        diff -= 1
    end
  else
    while diff != 0
        ptr2 = ptr2.next
        diff -= 1
    end
  end
  ```
- Now increment the head pointer of both the lists by one, at each step check if the lists have overlapped by checking if

 ```ruby
  while ptr1 != ptr2
    ptr1 = ptr1.next
    ptr2 = ptr2.next
  end

  return ptr // overlapping node
  ```

## Time complexity
- O(n) to traverse the first list twice
- O(m) to traverse the second list twice
- O(m+n) overall complexity


