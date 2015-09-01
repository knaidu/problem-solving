# Design distributed throttling
You have n machines that are crawling websites, implement throtting such that each crawler does
not crawl more than x pages from a particular host

## Solution
- Use a permission server in addition to the crawler server
- This would keep track of the number of pages downloaded by any crawler during a given time
  period, and then approve or deny a new crawl request
- Every crawler must first acquire permission befoew crawling the page, if denied, it should
  wait download
- To prevent the permission server from becomming a bottle-neck we can have multiple servers and
  use a hash to distribute the requests
- The permission algorithm could be a simple tll based key, which would be the last time
  a page was downlaoded from a server, if the ttl has not expired then permission denied
