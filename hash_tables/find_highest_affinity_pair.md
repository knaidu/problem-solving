# Find highest affinity pair
Write a program that takes as input a log file, each line in the file represents web views i.e
website_name, user_id. The affinity of a pair of pages is the number of distinct users who viewed
both pages. Given a log file return the websites that have highest affinity.

## Solution
- Parse over the log file and create a hash map if website -> visited useres
- Find the intersection of all pair of websites, and keep track of the largest intersection so far

## Code
```ruby
def highest_affinity_pair(file)
    hash = {}
    while !file.end?
        line = file.read_next_line
        website, user = line.split(',')
        if hash[website]
            hash[website].append(user)
        else
            hash[website] = [user]
        end
    end

    # Find intersection
    max_intersection_size = 0
    max_affinity_pair = {}
    hash.each do |website1, list1|
        hash.each do |website2, list2|
            if website1 != website2
                intersection_size = intersection(list1, list2)
                if intersection_siz > max_intersection_size
                    max_intersection_size = intersection_size
                    max_affinity_pair = {website1, website2}
                end
            end
        end
    end

    max_affinity_pair
end
```

## Complexity
- Time: O(n) to populate hash, O(n^2) to find highest affinity pair, where n is the number of websites
