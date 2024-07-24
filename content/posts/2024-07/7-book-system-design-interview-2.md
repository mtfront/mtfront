---
title: "读《System Design Interview Volume 2》"
author: 椒盐豆豉
type: post
date: 2024-07-23T23:53:00-07:00
url: /book-system-design-interview-2/
categories:
  - 喜欢就买
  - 重启电脑
tags:
  - software engineer
  - career 
  - reading
  - 导读
  - code
booktoc: true
bookComments: true
image: https://miro.medium.com/v2/resize:fit:1400/1*HQlYYpS4PD7E5CNqHUlX-w.jpeg
imageDes: "图源：https://medium.com/javarevisited/what-i-learned-from-the-book-system-design-interview-an-insider-guide-77562e48cdaa"
---

上回说到我激情读完码农 system design 面试准备必备手册[「优秀简笔画火箭教程 System Design Interview」]({{< relref "/posts/2024-07/3-book-system-design-interview-1" >}})，案例很经典也深入浅出比网上零散看视频准备系统很多，于是立刻激情买了 [volume 2](https://amzn.to/4cZmtGh)。今天草草翻完了。

为什么是草草翻完呢，因为看了几章发现远不如第一本有概括性，许多案例都非常需要 domain knowledge，这种东西你做过的话大概看一遍是很好的复习，但如果不是真的相关组的话也基本不可能问，如果没做过硬背书去面试也得跪，就比第一本满地高频的 niche 很多了。全书 13 章 400 多页基本只有 Proximity Service 和 Hotel Reservation 比较普适，稍微跟游戏沾点边的公司的话 Gaming Leaderboard 那章也可以看看。倒是 `Geohashing` 和 `Sorted Set (skip list)` 等几个知识点值得一学。但如果已经知道这几个关键字了直接去网上找相关资料即可没必要买全书。

面试的话还是建议精读[第一本](https://amzn.to/3LlsYre)。第一本和第二本不是递进关系只是不同案例，第一本的案例高频多了还囊括了一些高频基础知识。本来想说有用的东西没第一本书多就不发读书笔记了，不过像[第一本的读书笔记]({{< relref "/posts/2024-07/3-book-system-design-interview-1" >}})一样，反正写一遍笔记是我自己的复习过程，从 notion 里复制过来又不需要单独排版，索性直接发上来好了。只把我觉得有代表性的 Proximity Service 全章写了笔记，其它零散的知识点我单提出来了。

<!--more-->

{{< neodb "https://neodb.social/book/3qw7UcploI7yANxpvhH4cQ" 6 "https://amzn.to/4cZmtGh"  >}}

## 目录
把全书原本目录列下来方便大家参考去搜关键词。
1. Proximity Service
2. Nearby Friends
3. Google Maps
4. Distributed Message Queue
5. Metrics Monitoring and Alerting System
6. Ad Click Event Aggregation
7. Hotel Reservation System
8. Distributed Email Service
9. S3-like Object Storage
10. Real-time Gaming Leaderboard
11. Payment System
12. Digital Wallet
13. Stock Exchange

## Chapter 1. Proximity Service

### Step 1 - Understand the Problem and Establish Design Scope

- Can user specify the **search radius**? If not enough businesses, does the **system expand** the search?
- What’s **maximal radius** allowed?
- How does business information get added, deleted or updated? Do we reflect these operation in **real-time**?
- User might be moving while using the app. Do we refresh?

Non-functional requirement:

- Low latency
- Data privacy
- High availability and scalability. Can handle **spike in traffic** during peak hours in **densely populated areas**

### Step 2 - High-level design

**API Design**

- `GET /v1/search/nearby` (latitude, longitude, radius)
- `GET/POST/PUT/DELETE /v1/businesses/:id` (post doesn’t include id)

**Data model**

- Read/write ratio: **read-heavy. Relational database** can be good fit.
- Data schema: business table and geospatial(geo) index table

**High-level design**

- Load balancer
- Location-based service (LBS)
- Business service
    - Business owners create, update or delete. Mainly write. QPS not high
    - Customer view. QPS high during peak hour
- Database cluster: primary-secondary setup. primary handles all the write. **Strong consistency not required**.
- Scalability of business service and LBS: both stateless, easy to auto scale. Can setup regions and availability zones for further improvement.

**Algorithms to fetch nearby businesses**

- Existing geospatial databases such as **Geohash in Redis** or **Postgres with PostGIS extension**. You’re not expected to know the internals of those geospatial databases during an interview. It’s better to **demonstrate your problem-solving skills and technical knowledge by explaining how geospatial index works, rather than to simply throw out database names.**
- Common algorithms:
    - Hash: even grid, geohash, cartesian tiers
    - Tree: quad tree, Google S2, RTree
    - High level idea is the same: **to divide the map into smaller areas and build indexes for fast search**.
- Option 1: Two-dimensional search. Not efficient because we need to scan the whole table. Building indexes on longitude and latitude won’t help much. **Database index can only improve search speed in one dimension**.
- Option 2: Evenly divided grid: major issue: **distribution of business is not even**.
- Option 3: **Geohash**
    - Works by **reducing the two-dimensional longitude and latitude data into a one-dimensional string of letters and digits**.
        - Divide the planet into four quadrants (00, 01, 10, 11)
        - Divide each grid into four smaller grids, each by alternating between longitude bit and latitude bit
        - Repeat this subdivision until grid size is within the precision desired. Use **base32** representation. Normally precisions (levels) between 4 and 6 is what we want.(49.1km * 19.5km ~ 1.2km * 609.4m)
    - Boundary issues
        - Two locations can be very close but not shared prefix at all, (e.g. at equator), or have long shared prefix but belong to different geohashes.
        - Common solution is to fetch all businesses not only within the current grid but also **from its neighbors**. Neighbors can be calculated in constant time.
    - Not enough business: can only return within radius, or increase search radius until find (remove last digit of geohash)
- Option 4: **Quadtree**
    - Build an **in-memory tree** also recursively subdividing into four quadrants (grids). Runs on every LBS server, built at server start-up time.
    - Data on internal node: top left coordinates and bottom right coordinates; pointer’s to 4 children
    - Operational considerations:
        - May take a few minutes to build a quadtree with 200 million business at server start time. Should **roll out new release incrementally** to a small set of servers at a time.
        - How to update quadtree as businesses:
            - incrementally rebuild the quadtree, a small subset of servers at a time. Some server may return stale data but it’s fine. Can set up business requirement will only be effective next day. Can update cache using nightly job.
            - update on the fly will complicate the design, require locking mechanism.
- Option 5: Google S2
    - Also in-memory solution, maps a sphere to a 1D index based on the Hilbert curve. Complicated, not expect to go into details. Widely used (Google maps, Tinder)
    - Great for geofencing because it can convert arbitrary areas with varying levels. Allows us to define perimeters that surround the areas of interest and to send notifications to users who are out of the areas. Can provide richer functionalities than just returning nearby business.
- Geohash vs quadtree
    - Geohash
        - Easy to use and implement. No need to build a tree
        - Supports returning businesses within a specified radius
        - Precision (level) of geohash is fixed, the **size of grid is fixed** as well, cannot dynamically adjust the grid size based on population density. Need extra logic to support
        - **Updating the index is easy.**
    - Quad tree
        - Slightly harder to implement
        - Supports fetching k-nearest businesses (don’t care if business are within radius)
        - Can dynamically adjust the grid size based on population density
        - **Updating the index is more complicated** than geohash. **Rebalancing** the tree can also also complicated.

### Step 3 - Design deep dive

**Scale the database**

- Business table: sharding by business ID
- Geospatial index table
    - Option 1: For each geohash key, have array of business ID
    - Option 2: Each business ID for a row. Multiple businesses can have same geohash.
    - Recommend option 2 because for option 1, update a business need to scan whole array. Also need to lock teh row to prevent concurrent updates.
    - Scale: sharding is complicated. In our case everything can fit in the working set of a database server, **read replica** might be better fit.

**Caching**

- Cache key
    - Choosing coordinates as cache key for the user may be straightforward, but:
        - Location coordinates return from mobile phones are not accurate. Even user don’t move, result might be slightly different
        - User can move from one location to another slightly, change is not meaningful
    - Ideally, small changes in location should still map to the same cache key. Geohash & quadtree handles this well.
- Types of data to cache
    - List of business IDs in a grid
    - Business data need to render pages on the client

**Region and availability zones**

- Makes user physically closer to the system
- Gives us flexibility to spread traffic evenly across population
- Privacy laws

**Follow up question: filter results by time or business type**

Returned from search result is relatively small. hydrate business and filter in service.

**Final design**

- Get nearby business
    - Client sends user location and radius to load balancer
    - Forwards request to LBS
    - LBS finds the geohash length that matches the search
    - LBS calculates neighboring geohashes and adds them to the list
    - LBS calls Geohash redis server to fetch corresponding business ID. Calls to fetch IDs for each geohash can be made in parallel
    - LBS fetches fully hydrated business information from Business info Redis server, calculates distances between a user and businesses, ranks them, and return result to client
- View, update, add or delete a business
    - All business-related APIs are separated from the LBS
    - Fetch from Redis cache, if not, from database and then store in Redis cache.
    - Nightly job update
    

## 零散知识点
### Nearby friends 能用到的一些 redis 相关
- **Redis TTL** for each entry can be useful for nearby friends location history cache
- **Redis Pub/sub** is very lightweight message bus. **Channels** in Redis Pub/Sub are very cheap to create. A modern Redis server with GBs of memory could hold millions of channels (also called topics). Inactive channel will take up small amount of memory but **will not consume any CPU or I/O** without updates.
    - Thus subscribes to each friend’s channel instead of subscribing when they become online can simplify design
    - Use more memory, but trading higher memory for simpler architecture is worth it in this case
- Current locations for nearby friends do not need to be durably stored.
- WebSocket servers scale: Before a node can be removed, all existing connections should be **allowed to drain**. We can mark a node as “draining” at the load balancer so **no new** WebSocket connections will be routed.
### Message queue
- Benefits
    - Decoupling
    - Improved scalability. Can **scale producers and consumers independently.**
    - Increased availability. One part of system goes offline does not bring down the other
    - Better performance. Makes asynchronous communication easy, producers can add messages to queue without waiting for response.
- Each topic partition operates in the form of FIFO queue. Keep the order of messages inside a partition. Position in partition is called an **offset**.
- Data storage
    - Write-heavy, read-heavy. No update or delete
    - Can persist in **Write-ahead log (WAL)**
        - Pure sequential read/write access pattern. Disk performance of sequential access is very good.
        - Large capacity, pretty affordable.
- Batching: critical to performance. **Tradeoff between throughput and latency**
- Data delivery semantics: At-most once; At-least once; Exactly once(complicated, high cost of performance)
### Storage system
- Block storage
    - present the raw blocks to server as a volume (physically attached to server or through network)
    - Cost high, performance high
    - good for virtual machines and high-performance applications like database
- File storage
    - Provides higher-level abstraction to make it easier to handle files and directories
    - Do not need to deal with the complexity of managing the blocks, formatting volume, etc
    - Great for sharing a large number of files and folders within an organization
- **Object storage**
    - **Sacrifice performance for high durability, vast scale and low cost**. **Cold data** and is mainly used for archival and backup.
    - In a **flat structure**, no hierarchical directory structure. Can create a **logical hierarchy by concatenating the bucket name and object name to simulate a folder structure**.
    - Data access is normally provided via RESTful API.
    - Good for binary data, unstructured data.
    - Immutable, may have versioning.
    - **Bucket**: A logical container for object. Bucket name is globally unique.
    - Data organization:
        - No store each object in sand-alone file, because:
            - Wastes many data blocks. File system store files in discrete disk blocks, have same fixed size when volume is initialized. Small files could waste.
            - Could exceed system inode capacity.
        - We can **merge many small objects into a larger file**
            - Data node have: data file contains the object. **Starting offset** of the object. **Size of the object**.
            - No need to share this information across data nodes, can deploy a simple relational database in each data node.
    - Durability
        - Replication
        - **Erasure coding**: CHunks data into smaller pieces (placed on different servers) and create parities for redundancy. Slower access speed in exchange for higher durability and lower storage cost (than replication).
        - Correctness verification: checksum. A good checksum algorithm usually outputs a significantly different value even for a small change made to the input. e.g. md5, SHA1.
### Redis Sorted Set
- **A hash table and a skip list**. Ideal for game leaderboard.
- **Skip list** consists of a base sorted linked list and **multi-level indexes**.
    - e.g. Level 1 skip every 1 node. Level 2 skip every node for level 1.
    - **Add, find time complexity: O(log(n))**
- For scaling, partition on user ID needs merge and sort before returning. So maybe partition on sorted value, and have cron job analyze the distribution in each shard.
### Payment related systems
- **Reconciliation** process between internal services and external services is required. **Asynchronously verifies** that payment information across these systems is consistent.
- **Amount field is string** rather than number
    - Different protocols, software and hardware may support different numeric precisions in serialization and deserialization
    - Number could get extremely big or small
    - Only parse when used for display or calculation
- **Double-entry ledger system** is fundamental for any payment system and is key to accurate bookkeeping. Records every transaction into **two separate ledger accounts** with same amount. (e.g. buyer-debit-1, seller-credit-1)
- Handling payment delays: third party have update via webhook or we need to poll.
- Exactly once. **Idempotency** is key to ensure at-most-once. **UUID is commonly used.**

---

还是祝大家有又喜欢钱又多的工作！此外最近开始找工作了，有大西雅图地区或者 remote 的 staff+ level fullstack/backend software engineer opening 愿意提供 referral 机会的博友们欢迎留言或邮件我：）