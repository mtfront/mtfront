---
title: "优秀简笔画火箭教程——读《System Design Interview: An Insider's Guide》"
author: 椒盐豆豉
type: post
date: 2024-07-14T18:04:00-07:00
url: /book-system-design-interview-1/
categories:
  - 喜欢就买
tags:
  - software engineer
  - career 
  - reading
  - 导读
  - code
booktoc: true
compactToc: true
bookComments: true
image: https://miro.medium.com/v2/resize:fit:1400/1*HQlYYpS4PD7E5CNqHUlX-w.jpeg
imageDes: "图源：https://medium.com/javarevisited/what-i-learned-from-the-book-system-design-interview-an-insider-guide-77562e48cdaa"
---

准备面试时候看了被同侪们多次提到的的 Alex Yu 的 [`System Design Interview: An Insider's Guide`](https://amzn.to/3LlsYre)，比意料中实用。开始看头几章科普时候还会担心讲得太浅，到实际案例的时候就发现深度不错很适合一小时面试的 scope，而且意外还学到了些新东西，面试倾向的又不像 DDIA 挖那么深所以好读很多。选的案例也都很经典（除了最后两个个人觉得有点偏），而且有层层递进关系看得甚至有点小爽。书里给的 get buy in - estimate (这个环节我不喜欢) - dive deep - wrap up 的面试套路也挺有启发。总之全书看下来比零散地看没深度的 YouTube system design 讲解系统多了，立刻就去买了 [volume 2](https://amzn.to/4cZmtGh)。豆瓣短评里说简笔画火箭可太贴切了，但没办法就是要考，还是很实用的。

因为自己本来就要写一遍 bullet points 读书笔记作为给自己面试的复习材料，写都写了索性分享出来。

<!--more-->

{{< neodb "https://neodb.social/book/5NXZVS0Rb0RNRRV7UdATj3" 9 "https://amzn.to/3LlsYre"  >}}

因为是给自己的提示所以不会像以往的读书笔记一样加很多解释性语言和摘抄，会更简短一些。不过有些书在不同地方提到知识点我可能有移动和合并方便自己复习。有需求的朋友们还是建议先去看[原书](https://amzn.to/3LlsYre)，本读书笔记只能作为看过原书之后的复习。

此外小注释是他的方法里其实反复提到 back-of-the-envolpe estimate，即合理估算系统的 scale 给出一些数字，我个人不是很喜欢这个环节，面试多年也未遇到过有想考这个的，于是在很多章节的笔记里略去了。

## Forward
前言没有复习的干货，但是有一个作者注释觉得值得一提。

> In English, using “she” flows better than “he or she” or jumping between the two. To make reading easier, we use the feminine pronoun throughout this book. No disrespect is intended for male engineers.

## Chapter 1: Scale from zero to millions of users
### Which databases to use

- Relational database or SQL database
    - MySQL, Oracle, PostgresSQL
    - 40 yrs history, best for most
- Non-relational or NoSQL
    - Cassandra, DynamoDB, CouchDB, Neo4j, HBase
    - Right choice if your service:
        - **super-low latency**
        - data are unstructured
        - only need to serialize and deserialize data (JSON, XML, YAML)
        - **massive amount of data**

### Vertical scaling vs horizontal scaling

- vertical: scale up, adding more power (CPU, RAM to your server)
    - has hard limit, impossible to add unlimited cpu and memory
    - does not have failover and redundancy
- horizontal: scale-out, adding more server
- Load balancer evenly distributed traffic among servers
- Database replication
    - better performance
    - reliability
    - high availability

### Cache

- when data is **read frequently but modified infrequently**
- **expiration policy** (performance vs stale)
- **consistency**, keep data store and cache in sync
- mitigating failures (avoid single point failure, multiple cache server, overprovision the required memory)
- **eviction policy**: once cache is full, any adding might cause existing items to be removed, **LRU LFU**

### Content delivery network (CDN)

- cost (run by third party, consider moving infrequently used assets out of CDN)
- cache expiry
- CDN fallback (if there’s temporary CDN outage, client should detect and request resources from origin)
- invalidating files
    - API provided by CDN vendors
    - object versioning

### Stateless web tier

- stateful server remembers client data (state)
- stateless web servers shares database, Memcached/Redis. **easier to scale**

### Data centers

- geoDNS-routed (geo-routed) to closest data center
- geoDNS is a DNS service allows domain names to be resolved to IP based on location of user
- challenges:
    - traffic redirection
    - data **synchronization**. in case of **failover**, reroute to different data center. e.g. Netflix’s async multi-data center replication
    - **test and deployment**. test at different location

### Message queue

- durable component, **stored in memory**, supports **asynchronous communication**
- serves as **buffer** and **distributes** async requests
- **decoupling producer from consumer**
- producer and consumer can be **scaled independently**

### Logging, metrics, automation

- **aggregate logs** to centralized service
- collecting metrics help gain business insights and understand health status of system

### Database scaling

- vertical scaling drawbacks:
    - hardware limits
    - greater risk of **single point of failures**
    - cost high
- horizontal scaling
    - when choosing a sharding key, one of most important criteria is to choose a key that can **evenly distributed data**
    - resharding data needed when
        - single shard could no longer hold more
        - certain shards experiencing exhaustion faster than others due to uneven data distribution
    - celebrity problem aka **hotspot key problem** (allocate a shard to each celebrity which might require further partition)
    - **join and de-normalization** (de-normalize data so queries can be performed in a single table)

### Millions of users and beyond (summary)

- keep **web tier stateless**
- build **redundancy** at every tier
- cache data as much as you can
- support multiple data centers
- host static assets in CDN
- scale your data tier by **sharding**
- split tiers into individual services
- **monitor** your system and use **automation** tools

## Chapter 2: Back-of-the-envelope estimation

### Power of two

- Byte = 8 bits, ASCII character = 1 byte
- approximate value

| power | approximate value | full name | short name |
| --- | --- | --- | --- |
| 10 | 1 thousand | 1 Kilobyte | 1 KB |
| 20 | 1 million | 1 Megabyte | 1 MB |
| 30 | 1 billion | 1 Gigabyte | 1 GB |
| 40 | 1 trillion | 1 Terabyte | 1 TB |
| 50 | 1 suadrillion | 1 Petabyte | 1 PB |

### Latency numers every programmer should know

ns = nanosecond, µs = microsecond, ms = millisecond

1 ns = 10^-9 seconds

1 µs = 10 ^-6 seconds

1 ms = 10^-3 seconds

| Operation name | Time |
| --- | --- |
| L1 cache reference | 0.5 ns |
| Branch mispredict | 5 ns |
| L2 cache reference | 7 ns |
| Mutex lock/unlock | 100 ns |
| Main memory reference  | 100 ns |
| Compress 1KB with Zippy | 10 µs |
| Send 2KB over 1 Gbps network | 20 µs |
| Read 1 MB sequentially from memory | 250 µs |
| Round trip within same datacenter | 500 µs |
| Disk seek | 10 ms |
| Read 1MB sequentially from network | 10 ms |
| Read 1 MB sequentially from disk | 30 ms |
| Send packet CA → Netherlands → CA | 150 ms |

conclusion:

- memory is fast but disk is slow
- **avoid disk seek if possible**
- simple compression algorithms are fast
- data centers are usually in different regions and takes time to send data between

### Availability numbers

Service level agreement (SLA). Uptime is traditionally measured in nines (99.9%, 99.99%…). More nines the better.

### Example: Estimate Twitter QPS and storage requirement

- Assumptions:
    - 300 million MAU
    - 50% use daily
    - Post 2 tweets per day on averate
    - 10% contains media
    - Data is stored for 5 years
- QPS estimate:
    - DAU = 300 million * 50% = 150 million
    - Tweets QPS = 150 million * 2 tweets / 24h / 3600 seconds ~= 3500
    - Peak QPS = 2 * QPS ~= 7000
- Media storage estimate:
    - Average tweet size:
        - id 64 bytes
        - text 140 bytes
        - media 1 MB
    - Media storage: 150 million * 2 * 10% * 1 MB = 30 TB / day
    - 5 year: 30 TB * 365 * 5 ~= 55PB

### Tips

- Rounding and **approximation**
- **Write down your assumptions**
- **Label your units**
- Commonly asked: QPS, peak QPS, storage, cache, number of servers

## Chapter 3: A framework for system design interviews

### Step 1 - Understand the problem and establish design scope

- Giving out answer quickly without thinking gives no bonus points
- **Answering without a thorough understanding of the requirement is a huge red flag**. There’s no right answer
- Ask the right questions, **make proper assumptions**, gather all the information needed to build a system
- Kick start question list:
    - What specific features are we going to build
    - How many user does the product have
    - How fast does the company anticipate to scale up? What’s anticipated scales in 3 months, 6 months, a year?
    - What is the company’s technology stack? What existing services you might leverage to simplify the design

### Step 2 - Propose high-level design and get buy-in

- **Ask for feedback**
- Draw box diagrams with key components. Might includes clients (mobile/web), APIs, web servers, data stores, cache, CDN, message queue, etc
- Do back-of-the-envelope calculations to evaluate if your blueprint fits the scale constraints （我不喜欢这一条）
- **Go through a few concrete use cases**. This will help you frame the high-level design
- Should we include API endpoints and database schema here? Depends. For large problems like “Design Google search engine”, might be to low level. For designing backend for a multi-player poker game, this is a fair game.

### Step 3 - Design deep dive

At this step you and interviewer **already** achieved following objectives:

- Agreed on the **overall goals and feature scope**
- Sketched out a **high-level blueprint** for the overall design
- Obtained **feedback** from your interviewer on the high-level design
- Have some initial ideas about **areas to focus on**

### Step 4 - Wrap up

A few directions:

- Interviewer might want you to identify the system **bottlenecks** and discuss potential **improvements**.
- **Recap** of your design
- **Error cases** (server failure, network loss)
- **Operation issues** How to monitor metrics and error logs, how to roll out system
- How to **handle next scale curve**

List of dos and don’s:

- Dos
    - **Ask** for clarification
    - Understand the **requirements**
    - There’s neither the right answer nor the best answer. Solution designed to solve for young startup is different than established company with millions of users
    - Let the interviewer know what you’re thinking. **Communicate**.
    - Suggest **multiple approaches** if possible
    - Once agree on blueprint, go into details on each component. **Design the most critical components first**.
    - Bounce ideas off the interviewer.
    - Never give up
- Don’ts
    - Don’t be **unprepared** for typical interview questions
    - **Don’t jump into a solution** without clarifying the requirements and assumptions
    - Don’t go into too much detail on a single component in the beginning. Give the **high-level design first** then drills down.
    - If you get stuck, don’t hesitate to ask for hints.
    - Again, communicate. **Don’t think in silence.**
    - DOn’t think your interview is done once you give your design. Ask for **feedback early and often.**

### Time allocation for each step

- Understanding the problem: 3 ~ 10 minutes
- High-level design: 10 ~ 15 minutes
- Dive deep: 10 ~ 25 minutes
- Wrap up: 3 ~ 5 minutes

## Chapter 4: Rate limiter

### Benefit of API rate limiter

- Prevent resource starvation caused by Denial of Service (DoS)
- Reduce cost
- Prevent servers from being overloaded

### Step 1 - Understanding the problem and establish design scope

Some questions to ask:

- Client-side or server side
- Based on IP, user ID or other properties
- Scale of the system
- Is it distributed environment
- Is it separate service or should it be implemented in application code
- Do we need to inform users who are throttled?

Requirements gathered:

- Accurately limit excessive requests
- Low latency
- As little memory as possible
- Distributed rate limiting
- Exception handling
- High fault tolerance (if there are problems with rate limiter, e.g. cache server goes offline, it does not affect the entire system)

### Step 2 - High-level design

**Where to put the rate limiter**

- Evaluate current technology stack
- Identify the rate limiting algorithm that fits your business needs
- If you have already used microservice and included an API gateway for authentication, PI whitelisting, etc, may add a rate limiter to the API gateway
- Build your own rate limiting service takes time. If don’t have resource, commercial API gateway is a better option

**Algorithms for rate limiting**

- **Token bucket** (Amazon and stripe)
    - A container with pre-defined capacity.
    - Tokens are put in the bucket at preset rates periodically. Once full, no more added.
    - Each request consumes one token
        - If there’s enough token, request goes through
        - Not enough token, request dropped
    - Takes two parameters:
        - Bucket size
        - Refill rate
    - How many buckets?
        - Different bucket for different API
        - If we need to throttle on API address, each IP address requires a bucket
        - If system have global limit, have global bucket shared by all requests
    - Pros
        - Easy to implement
        - Memory efficient
        - Allows a burst of traffic
    - Cons
        - Two parameters to configure, it might be challenging to tune them properly
- **Leaking bucket algorithm** (Shopify)
    - Similar to token bucket except that requests are processed at a fixed rate. Usually FIFO queue.
        - When requests arrives, check if queue is full.
        - If not full, added to queue
        - Full, drop request
        - Requests are pulled from the queue and processed at regular intervals
    - Two parameters
        - Bucket size (queue size)
        - Outflow rate (how many requests can be processed at a fixed rate, usually in seconds)
    - Pros
        - Memory efficient given the limited queue size
        - Requests are processed at a fixed rate therefore it is suitable for use cases that a stable outflow rate is needed
    - Cons
        - A burst of traffic fills up the queue with old requests, recent requests will be rate limited
        - Two parameters to configure
- **Fixed window counter algorithm**
    - Divides timeline into fix-sized time windows and assign a counter for each window
        - Each requests increment the counter
        - Counter reaches the pre-defined threshold, new requests will be dropped
    - Pros
        - Memory efficient
        - Easy to understand
        - Resetting available quota at the end of a unit time window fits certain use cases
    - Cons
        - Spike in traffic at edge of a window could cause more requests than allowed quota to go through
- **Sliding window log algorithm**
    - Keeps track of request timestamps in cache (e.g. sorted sets of Redis)
        - New request comes in, remove all outdated timestamps (order than start of the current time window)
        - Add new request timestamp to the log
        - If log size ≤ allowed count, accept request. Otherwise reject (timestamp still already added)
    - Pros
        - Very accurate. In any rolling window requests will not exceed rate limit
    - Cons
        - Consumes a lot of memory because **even when request is rejected, timestamp still might be stored in memory**
- **Sliding window counter algorithm**
    - Hybrid approach that combines fixed window counter and sliding window log. Requests in current window + requests in previous window * overlap percentage of the rolling window and previous window
    - Pros
        - Smooths out spikes in traffic because rate is based on the average rate of previous window
        - Memory efficient
    - Cons
        - Only works for not-so-strict look back window. It’s an approximation. (Not as bad as it seems. Cloudflare experiments only 0.003% of requests are wrongly allowed or rate limited among 400 million requests)

**High-level architecture**

- Where to store counters? In-memory cache. Redis is popular has two commands:
    - INCR: increases the stored counter by 1
    - EXPIRE: Sets a timeout for the counter.
- Workflow
    - Client sends request to rate limiting middleware
    - Middleware fetches counter from redis
        - if limit reached, reject
        - if not reached, request sent to API servers, meanwhile increment counter and saves back to redis

### Step 3 - Design deep dive

**Rate limiting rules**

Lyft open source example:

```yaml
domain: messaging  
descriptors:  
  - key: message_type  
    Value: marketing  
    rate_limit:  
      unit: day  
      requests_per_unit: 5
```

**Exceeding rate limit**

- APIs return a HTTP 429 (too many requests) to the client.
- Depending on use case, we may enqueue rate-limited requests to be processed later

**Rate limiter headers**

- `X-Ratelimit-Remaining`: remaining number of allowed requests within the window
- `X-Ratelimit-Limit`: the limit itself
- `X-Ratelimit-Retry-After`: number of seconds to wait

**Detailed design**

- Rules are stored on the disk. Workers frequently pull rules from disk and store them in cache
- When client sends request to the server, request is sent to rate limiter middleware first
- Middleware loads rules from cache, fetch counters and last request timestamp from Redis cache and decide

**Rate limiter in a distributed environment**

- Race condition
    - Locks - will slow down
    - Lua script
    - Sorted set
- Synchronization issue
    - ~~Use sticky sessions that allow a client to send traffic to the same rate limiter~~ (not advised)
    - Store in redis

**Performance optimization**

- **Multi-data center**, use close to user edge servers (cloud service providers)
- Synchronize data with **eventual consistency**

**Monitoring**

- Algorithm is effective
- Rules are effective

### Step 4 - Wrap up

Algorithms:

- Token bucket
- Leaking bucket
- Fixed window
- Sliding window log
- Sliding window counter

Some talking points if have remaining time:

- **Hard vs soft rate limiting**
- Rate limiting at **different levels (application, IP etc)**. Open systems interconnection model has 7 laters: 1. Physical. 2. Data link layer. 3. Network layer. 4. Transport layer. 5. Session layer. 6. Presentation layer. 7. Application layer)
- **Avoid being rate limited**. Design client with best practices:
    - Client cache
    - Understand limit and not send too many requests
    - Catch exceptions and errors to gracefully recover
    - Sufficient back off time to retry logic

## Chapter 5: Consistent hashing

### The rehashing problem

- if you have n cache servers, balance load using `serverIndex = hash(key) % N` will balance load.
- However when one server goes offline will cause a storm of cache misses.

### Consistent hashing

When hash table is re-sized and consistent hashing is used, **only k/n keys need to be remapped on average** (k = number of keys, n = numer of slots)

**Base hash space and hash ring approach**

- **Hash space and hash ring**: connects both ends of hash space get a ring
- Hash servers: using same hash function (SHA-1), **map server IP or name onto the ring**
- Hash keys: Using same hash function and **hash cache keys onto the hash ring**
- Server look up: **Go clockwise from the key position on the ring** until server is found
- **Add/remove a server:** only from the new server to next server need to be redistributed
- Problems:
    - Impossible to **keep the same size of partitions** on the ring for all servers considering a server can be added or removed. Can be very imbalanced.
    - Possible to have nonuniform key distribution on the ring. (If server are all mapped in part of the ring)

**Virtual nodes**

- **Each server is represented by multiple virtual nodes on the ring,** responsible for multiple partitions
- **Virtual node number tradeoff**: Standard deviation will be smaller when we increase number of virtual nodes, but more spaces are needed to store data about virtual nodes.

**Benefits** of consistent hashing

- **Minimized keys are redistributed** when servers are added or removed
- Easy to scale horizontally because data are more evenly distributed
- **Mitigate hotspot key problem**

## Chapter 6: Key-value store

### Understand the problem and establish design scope

- Size of key-value pair is small
- Ability to store big data
- High availability
- High scalability
- Automatic scaling
- Tunable consistency
- Low latency

### Distributed key-value store

**CAP** theorem

- **Consistency:** all clients see the same data at the stame time no matter which node they connect to
- **Availability**: Any client which requests data gets a response even if some nodes are down
- **Partition Tolerance**: A partition indicates a **communication break between two nodes**. Partition tolerance means the system continues to operate despite network partitions.

**Real-world distributed systems**

Key-value stores are classified based on two CAP characteristics: CP, AP, CA

**Partition cannot be avoided**, and when it occurs, we must **choose between consistency and availability.**

- CP (choose consistency over availability): **block all write**, make service unavailable. Bank systems usually have extremely high consistent requirement.
- AP (choose availability over consistency): accepting reads, event it might return **stale** data. Will be synced once network partition is resolved.

### **Data partition - consistent hashing**

- Distribute data across multiple servers evenly
- Minimize data movement when nodes are added or removed
- **Heterogeneity**: number of virtual nodes for a server is proportional to the server capacity. higher capacity server can be assigned more virtual nodes.

### **Data replication**

- To achieve high availability and reliability, data must be **replicated asynchronously** over N servers (configurable)
- Walk clockwise from key position choose first N servers to store data copies
- For better reliability, **replicas are placed in distinct data centers**

### Consistency

**Quorum consensus**

- N = number of replicas
- W = Write quorum size
- R = Read quorum size

Configure W, R, N is typical **tradeoff between latency and consistency.** if W + R > N: **strong consistency** (at least one overlapping node that has latest data to ensure consistency. 

**Consistency models**

- **Strong consistency**
    - any read returns a most updated write data item. **client never see out-of-date data.**
    - Achieved by forcing a replica not accept new reads/writes until every replica has agreed on current write.
    - Not ideal for highly available systems because it could block new operations
- **Week consistency**: subsequent read operations may not see the most updated value
- **Eventual consistency**
    - a specific form of weak consistency. Given enough time, all updates are propagated and all replicas are consistent.
    - Allows inconsistent values to enter the system
    - Force client to read the values to **reconcile**
    - Recommended for key-value store. Dynamo and Cassandra.

**Inconsistency resolution: versioning and vector clocks** 

- **Versioning** means treating **each data modification as a new immutable version** of data.
- **Vector clock** is a [server, version] pair associated with a data item. Used to check if one version precedes, succeeds, or in conflict with others.
    - Assuming D([S1, v1], [S2, v2], …[Sn, vn]), v is version s is server
    - When D is written to server Si, system must perform:
        - Increment vi if [Si, vi] exists
        - Otherwise, create a new entry [Si, 1]
    - Conflict: Sx writes [Sx, 1] but Sy writes [Sy, 1]
    - When client reads data and discover conflict (some version modified by two servers), resolve and send back.
    - Downsides:
        - **Add complexity to client** because need to implement conflict resolution logic
        - [server: version] pair can grow rapidly. We can set threshold for length and remove older. (Cannot decide accurately, but Dynamo paper hasn’t encountered this problem in production)

### Handling failures

**Failure detection**

Requires at least two independent sources of information to mark a server down. **Gossip protocol**:

- Each node maintain node list, contains ID and heartbeat counters
- Each node periodically sends heartbeats to a set of random notes, which in turn propagate to another set of nodes
- If the heartbeat has not increased for more than predefined periods, member is considered as offline

**Temporary failures**

- **Sloppy quorum:** Instead of enforcing the quorum requirement, system chooses first W healthy servers for writes and first R healthy servers for reads, offline servers are ignored
- **Hinted handoff:** if a server is unavailable, another server will process requests temporarily. When the down server is up, changes will be pushed back to achieve data consistency.

**Permanent failures**

- **Anti-entropy** protocol: comparing each piece of data on replicas and updating each replica to the newest version
- **Merkle tree (Hash tree)** is used for inconsistency detection and minimizing the amount of data transferred
    - Every non-leaf node is labeled with the hash of the labels or values (in case of leaves) of its child nodes
    - Allows efficient and secure verification of the contents of large data structures

**Data center outage:** Replicate data across multiple data centers

### System architecture

- Clients communicate with the key-value store through simple APIs: **get(key) and put(key, value)**
- Coordinator: a node acts as a proxy between the client and the key-value store
- Nodes are distributed on a ring using consistent hashing
- Completely decentralized so adding and moving nodes and be automatic
- Data is replicated at multiple nodes
- No single point of failure as every node has same set of responsibility
    - client API
    - failure detection
    - Conflict resolution
    - Failure repair mechanism
    - Replication
    - Storage engine

**Write path**

- Write request is persisted on a commit log file
- Data is saved in memory cache
- When memory cache is full data is flushed to **SSTable on disk** (sorted-string table is sorted list of <key, value> pairs)

**Read path**

If not in memory, need to be retrieved from disk. **Bloom filter** is used to find out which SSTable contains the key efficiently.

### Summary
### 

| Goal/Problems | Technique |
| --- | --- |
| Store big data | Consistent hashing to spread the load across servers |
| High availability reads | Data replication; Multi-data center setup |
| Highly available writes | Versioning and conflict resolution with vector clocks |
| Dataset partition | Consistent hashing |
| Incremental scalability | Consistent hashing |
| Heterogeneity | Consistent hashing |
| Tunable consistency | Quorum consensus |
| Temporary failures | Sloppy quorum and hinted handoff |
| Permanent failures | Merkle tree |
| Handling data center outage | Cross-data center replication |

## Chapter 7: Unique ID generator in distributed systems

### Step 1 - Understand the problem and establish design scope

Some questions to ask:

- What are the characteristics of unique ID (a: unique and sortable)
- Does the id only contain numerical values?
- Length requirement (64 bit, etc)
- Scale of the system

### Step 2 - High-level design and buy-in

**Multi-master replication**

- Use database’s auto_increment (by 1)
- Drawbacks:
    - Hard to scale
    - IDs do not go up with time across multiple servers
    - Does not scale when a server is added or removed

**UUID**

- 128 bit number
- Very low probability of getting collision
- Can be generated independently without coordination between servers
- Pros
    - Generating is simple, no coordination
    - Easy to scale because each server generating IDs they consume
- Cons
    - 128 bit does not fit requirement
    - IDs do not go up with time
    - Could be non-numeric

**Ticket server**

- Use a centralized auto_increment in a single database server (ticket server)
- Pros
    - Numeric IDs
    - Easy to implement, works for small to medium-scale applications
- Cons: Single point failure

**Twitter snowflake approach**

- Divide ID into different sections
    - **Sign bit: 1 bit.** always be 0, reserved for future uses. (distinguish between signed and unsigned numbers)
    - **Timestamp: 41 bits.** Milliseconds since the epoch or custom epoch.
    - **Datacenter ID: 5 bits**, 2^5 = 32 data centers
    - **Machine ID: 5 bits**, 2^5 = 32 machines per center
    - **Sequence number:** 12 bits. In each machine sequence number increment by 1. Number reset to 0 every millisecond.

### Step 3 - Design deep dive

- Timestamp**:** 2^41 milliseconds which is ~**69 years.**
- Sequence number: 2^12 = 4096 combination per millisecond on same server.

### Step 4 - Wrap up

some talking points:

- **Clock synchronization**: we assumed ID generation servers have same clock. night not be true when server is running on multiple cores. same challenge exists in multi-machine scenarios. **Network Time protocol**
- **Section length tuning**: depend on use case, change each section’s length.

## Chapter 8: Url shortener

### Step 1 - Understand the problem and establish design scope

questions list:

- Traffic volume
- How long is shortened URL (as short as possible)
    - Need to ask traffic volume / QPS to estimate length we need
- What characters are allowed?
- Can shortened URLs be deleted or updated

### Step 2 - High-level design

**API endpoints**

- URL shortening: `POST api/v1/data/shorten`
    - request parameter: `{longUrl: longURLString}`
    - return shortURL
- URL redirecting: `GET api/v1/shortUrl`
    - return longURL for http redirection

**URL redirecting**

- Status code
    - 301 redirect: permanently (cached by browser)
    - 302 redirect: temporarily
- http header `location`: longURL

**URL shortening**

Hash function that satisfy:

- longURL must be hashed to one hashValue
- Each hashValue can be mapped back to the longURL

### Step 3 - Design deep dive

**Data model**

- memory hash table: not scalable enough
- relational database: [id(auto_increment), shortURL, longURL]

**Hash function**

- Hash value length: [0-9, a-z, A-Z] = 62^n. 6 → 56 billion, 7 → 2.5 trillion
- **Hash + collision resolution**
    - Even shortest well-know hash function (CRC32, MD5 or SH-1) produce more than 7 characters.
    - We can take first 7 character but this will cause collision
    - We can recursively append predefined string to longURL and re-hash until there’s no more collision. However it’s expensive to query database to check if a shortURL exists for every request. Bloom filter can improve performance
- **Base 62 conversion**
    - 10 - a, 11 - b, 36- A, 61 - Z

Comparison

| Hash + collision resolution | Base 62 conversion |
| --- | --- |
| Fixed short URL length | Short URL length not fixed, goes up with ID |
| Does not need a unique ID generator | Depends on unique ID generator |
| Collision is possible and must be resolved | Collision is impossible |
| Impossible to figure out next available short URL because it does not depend on ID | It’s easy to figure out next available short URL. Security concern. |

### URL shortening deep dive

Use base 62 as it’s simple and functional. flow:

- longURL input
- System check if the longURL **exists** in the database
- If it is, converted before. fetch shortURL from database and return to client
- If not, generate new ID using unique ID generator
- Convert ID to shortURL with base 62 conversion
- Create database row with ID, shortURL and longURL

### URL redirecting dive deep

- User clicks short url
- Load balancer forwards the request to web servers
- If shortURL is already in cache, return longURL
- If not in catch, fetch longURL from database. if not in database, invalid shortURL

### Step 4 - Wrap up

additional talking points:

- rate limiter (prevent malicious user send large number of URL shortening request).
- web server scaling (stateless, easy to scale)
- database scaling (replication and sharding)
- analytics: (link click rate, when, etc)
- availability, consistency, reliability

## Chapter 9: Web crawler

### Crawler use case

- Search engine indexing
- Web archiving
- Web mining (discover useful knowledge from the internet)
- Web monitoring (copyright)

### Step 1 - Understand the problem and establish design scope

Basics:

- Given a set of seed URLs, download all the web pages addressed by the URLs
- Extract URLs from these web pages
- Add new URLs to the list of URLs to be downloaded

Questions:

- What’s the purpose of the crawler
- How many web pages does the crawler collect per month
- What content type are included, HTML only or other like PDFs and images
- Do we consider newly added or edited web pages
- Do we store HTML pages crawled from the web
- How do we handle web pages with duplicate content

Good crawler characeristics:

- **Scalability**. Should be extremely efficient using parallelization.
- **Robustness** (bad HTML, malicious links, etc)
- **Politeness**. Should not make too many requests to a website within short time.
- **Extensibility**. support new content types.

### Step 2 - High-level design

- **Seed URLs.** General strategy: **divide the entire URL space** into smaller ones, like country and topics. Think out loud, no perfect answer.
- **URL frontier.** Split crawl state into two: **to be downloaded** and **already downloaded.** To be downloaded is called **URL frontier.** It’s a **FIFO queue.**
- **HTML downloader**. Download URLs provided by URL frontier
- **DNS resolver**
- **Content Parser**. Malformed web pages could provoke problems and waste storage space.
- **Content Seen?** Avoids duplicate. **Compare hash value.**
- **Content storage**
    - Most on disk
    - Popular content store in memory
- **URL Extractor. Parses and extracts links from HTML page**
- **URL filter**. filter certain content types, file extensions, error links and balcklisted sites.
- **URL Seen?** keeps track of URL visited before or already in the frontier. Bloom filter and hash table.
- **URL storage**. store visited URLs.

**Workflow**

- Add seed URLs to URL frontier
- HTML downloader fetches URLs from frontier
- Content parser parse HTML and checks if pages are malformed. After parsing and validation passed to content seen.
- Content seen checks if HTML page already in storage if so discarded. If not pass to link extractor
- Link extractor extracts links
- Extracted links passed to URL filter
- After filtering, passed to URL seen? component
- If not seen, added to URL frontier

### Step 3 - deep dive

**URL frontier**

- **DFS vs BFS.** Mostly use BFS using FIFO queue. Two problems:
    - Most links are linked back to same host. Easy to overwhelm host and it’s impolite.
    - Standard BFS does not take priority into consideration. (page ranks, traffic, update frequency, etc)
- **Politeness** - download one page at a time from the same host. Add delay
    - Map website hostnames to download worker threads. Each thread has a separate FIFO queue only download URLs obtained from that queue.
    - Queue router: ensures each queue only contains URLs from same host (mapping table)
    - Queue selector: map worker to one queue
    - Add delay in each worker
- **Priority**
    - **Prioritizer**: Takes URLs and computes priorities
    - Queue 1 to n has assigned priority. Queues with high priority are selected with higher probability
    - Queue selector: randomly choose a queue with bias towards queues with higher priority
- Combined, we have:
    - Front queues: manage prioritization
    - Back queues: manage politeness
- **Freshness**
    - Recrawl based on web pages update history
    - Prioritize URLs and recrawl important pages first and more frequently
- **Storage for URL frontier:** Hybrid: majority on disk, maintain buffers in memory for enqueue/dequeue. Data in buffer is periodically written to the disk.

**HTML Downloader**

- **Robots.txt**. Check and follows its rules.
- **Performance optimization**
    - Distributed crawl.
    - **Cache DNS resolver**. DNS resolver is bottleneck. Periodically update by cron jobs
    - **Locality**.
    - **Short timeout**. avoid block by a slow site.
- **Robustness**
    - Consistent hashing
    - Save cral states and data
    - Exception handling
    - Data validation
- Extensibility: plugin new downloader module to download new content types
- **Detect and avoid** problematic content
    - Redundant (check hash)
    - Spider traps (might require manual verification)
    - Data noise. (ads, code snippets, sapm URLs)

### Step 4 - Wrap up

additional talking points:

- Server-side rendering. If download directly won’t be able to retrieve link. Do server-side rendering (dynamic rendering) first before parsing a page.
- Filter out unwanted pages.
- Database replication and shardinng.
- Horizontal scaling.
- Availability, consistency, relability.
- Analytics.

## Chapter 10: Notification system

### Step 1 - Understand the problem and establish design scope

Question list:

- What types of notification does the system support (**mobile push, SMS, email**)
- Is it real time? (soft real, want to receive ASAP, but if under high load, a slight delay is acceptable)
- Supported devices (cuz iOS and android have different push system)
- What triggers notifications (can be triggered by client or server side)
- Will user be able to opt-out
- How many notifications are sent out each day

### Step 2 - High-level

**Different types of notification**

- iOS push notification
    - Provider: A provider builds and sends notification request to **Apple Push Notification Service (APNS)** with following data:
        - Device token
        - Payload (json dictionary)
    - APNS: provided by Apple
    - iOS Device: end client that receives notifications
- Android push notification: Firebase Cloud Messaging (FCM) provided by google or local ones
- SMS message: **third party SMS service** like Twilio, Nexmo
- Email: even can setup own, many use **commercial email services** like Sendgrid and Mailchimp, which offers **better delivery rate and data analytics**

**Contact info gathering flow**

- Gather mobile device tokens, phone numbers or email address
- when user install or sign up
- API servers collect user contact info and store in database

**Notification sending/receiving flow**

**High-level design**

- Services trigger notif by calling notification system
- Notification system: centerpiece of sending/receiving.
    - providing **APIs for services to call**
    - query database or cache to fetch data
    - **basic validation** to verify emails, phone numbers
    - **build notification payloads** for third party services
    - **enqueue** messages
- Cache / DB
    - User contact info
    - Notification log database
- Message queues. each type assigned to a dedicated queue
- Third-party services worker. **Good extensibility** (different location might have different service)
- iOS, Android, SMS, Email: receiving notif

### Step 3 - Design deep dive

**Reliability**

- How to prevent data loss: Persist notification in **notification log database**
- **Dedupe**: before sending out, check if eventID is seen before

**Additional components**

- Notification service
    - **Notification setting**: opt-in/outs
    - **Rate limiting**: avoid spamming user.
    - Security in push notification: Only authenticated or verified clients can send.
- Third party workers
    - Notification template: preformatted notification for parameters, styling and tracking, etc
    - **Retry mechanism**: when third-party service fail. detection to involve developer
- **Monitor queued notification**
- **Event tracking (analytics service)**

### Step 4 - Wrap up

Additional talking points:

- Reliability
- Security
- Tracking and monitoring
- Respect user settings
- Rate limiting

## Chapter 11: News feed system

### Step 1 - Understand the problem and establish design scope

- What are the important feature (publish post and see friends’ posts)
- Is it sorted by **reverse chronological order** or have any other ranking
- How many friends can user have
- Traffic volume
- Can feed contain images, videos or just text

### Step 2 - High-level design

**Newsfeed APIs**

- Publishing `POST /v1/me/feed`
    - content
    - auth_token
- Retrieval `GET /v1/me/feed`
    - auth_token

**Feed publishing**

- Client call API
- Web servers redirect traffic to internal services
- Post service: persist data in db and cache
- Fanout service: push new content to friends’ newsfeed
- Notification service: inform frends

**Newsfeed building**

- Client: request to retrieve
- Load balancer redirect traffic to servers
- Fetches newsfeed from cache
- Cache: stores IDs need to be fetched

### Step 3 - Deep dive

**Feed publishing**

- Web servers:
    - Validate user token
    - Rate limit posts user can make
- Fanout service
    - On write: feed pre-computed during write time
        - Pros:
            - generated in real-time and can be pushed to friends immediately
            - Fetching newsfeed is fast
        - Cons:
            - Hotkey problem. User has many friends slow.
            - Inactive users wasting resources.
    - On read: generated during read time. on0demand model.
        - Pros:
            - Inactive users not wasting resource
            - No hotkey problem
        - Cons: fetching is slow
    - We should adopt hybird approach. for celebrities fetch on read, others on write.

**Cache architecture**

- News Feed: stores IDs of news feeds
- Content: Stores every post data. Popular content is stored in hot cache
- Social graph: user relationship data
- Action: whether user liked, replied or took other actions on a post
- Counters: stores counters for like, reply, follower, following etc. **(discussion about inconsistency?)**

### Step 4 - Wrap up

Other talking points:

- Scaling the database
    - Vertical scaling vs horizontal scaling
    - SQL vs NoSQL
    - Master-slave replication
    - Read replicas
    - Consistency models
    - Database sharding
- Other talking points:
    - Web tier stateless
    - Cache data as much as you can
    - Support multiple data centers
    - Lose couple components with message queues
    - Monitor key metrics
  
## Chapter 12: Chat system

### Step 1 - Understanding the problem and establish design scope

- 1 on 1 or group based?
- Scale of the app
- Group member limit?
- Features, attachment? (1 on 1, group, online indicator, only suuports. text, etc)
- Message size limit
- Is it end-to-end encryption required
- How long shall we store the chat history

### Step 2 - High-level

**Connection types**

- ~~Polling~~ (consumes server resource when most of the time answer is no new message)
- Long polling: holds connection open until there’s actually new messages or timeout. **Drawbacks**:
    - Sender and receiver may not connect to the same chat server
    - Server has no good way to tell if a client is disconnected
    - Inefficient. user does not chat much still waste resource.
- **WebSocket**
    - Most common solution for sending asynchronous updates from server to client
    - Initiated by client, starts as a HTTP and “upgraded” by handshake to WebSocket connection.
    - Persistent connection, **server could send updates to a client**

**High level design**

- **Stateless services**: traditional public-facing request/response services, manage login, signup, user profile, etc.
    - **Service discovery**: Primary job is to **give the client a list of DNS host name of chat servers to connect to.**
- **Stateful service (chat service)**
    - Stateful because each client maintains a persistent network connection to a chat server
    - Client **does not switch to another server** as long as service is still available
    - Service discovery coordinates closely with chat service to avoid server overloading
- Third-party integration: **push notification**
- **Presence servers** manage online/offline status
- **Key-value store** persist chat history
    - Requirement
        - Amount of data is enormous
        - **Only recent chats accessed frequently**
        - User still need to require random access of data ,e.g. search, mentions, jump to specific messages
        - Read to write ration is close to 1:1
    - Why key-value store
        - Easily horizontal scaling
        - Low latency access
        - Relationship do not handle long tail data well. Indexes grow large ,random access is expensive
        - FB(HBase) and Discord(Cassandra)

**Data models**

- Message Id: Unique, Sortable by time
    - ~~auto_increment~~, NoSQL databases usually do not have
    - Global 64-bit like Snowflake
    - **Local sequence number generator**: Maintain sequence within a channel is sufficient. **Easier to implement in comparison to global ID**.
- 1 on 1 chat
    - message_id (primary key)
    - Cannot rely on created_at to decide sequence becaseu two messages can be created at same time
    - mesage_from, message_to, content
- Group chat
    - channel_id, message_id (primary key)
    - channel_id is the partition key because all queries in a group chat operate in a channel

### Step 3 - deep dive

**Service discovery**

- User log in, load balancer send request to API servers
- Authenticates user, service discovery finds best chat server
- User connects to chat server through WebSocket

**Message flows**

- 1 on 1
    - A sends chat to chat server 1
    - chat server 1 obtains message ID from ID generator
    - server 1 send message to message sync queue
    - Message stored to key-value store
    - if B’s online, chat server 2 pulls message and sends to B
    - If B’s offline, push notification sent from push notification servers
- Message synchronization across multiple devices
    - Each device maintains a `cur_max_message_id` keeps latest on device
    - New message: recipient ID == logged-in user, message_id in key-value store is larger than cur max
- Small group chat flow
    - Message from user A is **copied to each group member’s sync queue**
    - each client only needs to check its own inbox to get new message

**Online presence**

- User login: After websocket connection is built, user’s `last_active_at` saved in the KV store
- User logout: status changed to offline in KV store
- User disconnection
    - Periodically, online client sends heartbeat event to prescence servers
    - If it’s older than x seconds, consider offline
    - Set long enough heartbeat missed threshold to avoid flipping back and forth
- Online status fanout
    - publish-subscribe model, each friend pair maintains a channel
    - for larger group, informing all members is expensive, fetch online status only when a user enters a group or manually refreshes the friend list

## Chapter 13: Search autocomplete system

### Step 1 - Understanding the problem and establish design scope

**Questions**

- Is matching only supported at the beginning of a search query or in the middle as well
- How many autocomplete suggestions should the system return
- How does system know which 5 to return
- Are search queries in English
- Do we allow capitalization and special characters
- How many users

**Requirements**

- Fast response time
- Relevant
- Sorted (by popularity or other ranking model)
- Scalable
- Highly available

### Step 2 - High-level design

**Data gathering service: keep frequency table and update**

**Query service**

### Step 3 - Deep dive

**Trie data structure**

- Tree-like data structure
- Root represent empty string
- Each node stores a character and 26 children of every possible character
- Each tree node represents a single word or prefix string
- Frequency is also included in nodes
- Time complexity: p (length of prefix), n (total number of nodes), c (number of children of given node)
    - Find the prefix: O(p)
    - Traverse subtree from prefix node to get all valid children: O(c)
    - Sort children and get top k: O(clogc)
- Optimization:
    - **Limit the max length of a prefix**
    - **Cache top search queries at each node** (trading space for time)
    - New complexity: find prefix and return top k is both O(1)

**Data gathering service**

- **Updating data in real time is not practical** because:
    - Users may enter billions of queries per day, updating in realtime slows down query service
    - **Top suggestions may not change** much once the trie is built
- **Analytics Logs**: Stores raw data about search queires (append-only and not indexed)
- **Aggregators**
    - Aggregate data to be better processed by our system
    - For real-time applications like twitter, aggregate data in shorter time interval. For google maybe not much
    - Aggregated data ([query, time, frequency])
- **Workers**: perform asynchronous job at regular intervals. Build trie and store it in Trie DB
- **Trie Cache**:
    - Distributed cache system that keeps trie in memory for fast read.
    - Takes weekly snapshot of the DB
- **Trie DB**. two options:
    - Document store: periodically take a snapshot and serialize. MongoDB
    - Key-value store: pre-fix is mapped to a key. Data on each node is mapped to a value in hash table

**Query service**

- Workflow
    - Search query sent to load balancer
    - The load balancer routes the request to API servers
    - API servers get trie data from Trie cache and construct response for client
    - If data not in Trie cache, replenish data back to the cache
- Optimization
    - **AJAX request** (sending/receiving a request/response does not refresh the whole web page)
    - **Browser caching** (for example Google caches 1 hour)
    - **Data sampling** (Only 1 out of every N request is logged by the system)

**Trie operations**

- Create: by workers using aggregated data.
- Update
    - option 1: update trie weekly. once a new trie created, replace old one
    - option 2: update individual trie node directly (slow, if site is small then acceptable)
- Delete
    - Add **filter layer** to filter out unwanted suggestions
    - Unwanted suggestions are removed physically from database asynchronically so correct data set will be used to build trie next update.

**Scale the storage**

Look at historical data volume to do smart sharding

### Step 4 - Wrap up

Follow up questions:

- Support multiple languages: store Unicode characters in tire node
- What if top search queries in one country are different from others: build different tires for different countries. store tries in CDNs
- How can we support treading (real-time) search queries?
    - Reduce working data set by sharding
    - Change ranking model and assign more weight to recent search queries
    - Streaming data (a different architecture)

## Chapter 16: The learning continues
（第 14 和 15 章是 Design YouTube 和 design Google drive，涉及很多视频存储和文件压缩的 domain knowledge，跟我自己不太相关，所以这里没有列出，感兴趣的朋友可以自己去读[原书](https://amzn.to/3LlsYre)。

这一章里作者列出了很多原文参考的现实世界系统设计真实案例文章和 engineering blog，不过仅仅过去三年很多链接就失效了，这里就不一一列出了，网上应该很容易搜到。

附加推荐了三本书倒是可以看看：
- [`Understanding Distributed Systems` ](https://amzn.to/3Wk7nWw) by Roberto Vitillo
- [`The Tech Resume Inside-Out`](https://gumroad.com/a/638055539)  by Gergely Orosz
- [`Designing Data-Intensive Applications`](https://amzn.to/3Y48Y0v) by Martin Kleppmann。大名鼎鼎的 DDIA 应该没人还没看过吧……上次找工作的时候我就终于把吃灰多年的它啃完了。相比本书 DDIA 深度更深，不过读起来比针对面试复习的本书更艰涩一点。如果是以准备面试为目的的话还是建议先读本书，感兴趣再去读 DDIA。

## 记后感
发现我自己极为高效的学习方法就是把学习笔记当博客发。就比如我看书如果是看学习的书本身可能是拖拖拉拉，但我这周末想想复习这本书写读书笔记然后发博客，效率拔群了简直，之前断断续续看了一个月的书这一天半就写完了，还没影响出去吃了回饭散步外加晚上出去看 show 和第二天出去游了个泳，而且详细程度确实也感觉又看了一遍书，还产生了直接可以当小抄跳转的读书笔记（notion 复制出来直接是 markdown 真是太方便了）。以后感觉边看边写笔记得了（但第一遍看应该看不了这么快倒是）。

（当年我第一次在本校成为出圈小网红还是写毛概笔记成了打印店热销材料 be like 王后雄，十几年过去了我竟然还在写复习资料，人生是个圈（？）

另一个发现是，虽然平时拧螺丝面试造火箭大多数时候是实情，但是经过在不同公司呆多了发现实际工作中学到的一些知识还是能在面试中见到的。

比如年轻时候被问到 design chat app 这种题就只会画个极度简笔画能说出来 socket 和 message queue 糊弄就不错了，但是在某 chat app 公司呆过之后再复习的时候看到 stateless web tier + stateful service 的时候就突然一拍大腿恍然领悟，哦这不是去年把我整的要死要活写出一坨屎的 elixir code 在干的事儿嘛！！！！比什么瞎套 queue 的 make sense 多了啊！就作为不爱搞技术虽然干了这么多年但基本都在产品层的人，以前看到 stateless 和 stateful 随便就过去了也没深刻理解 why，当你被它折磨过半年之后 it all make sense 啊！！！ 

当然也就是小公司会 cover 这么大 scope 了，毕竟在某 SNS 公司干过活儿但要是碰到 design newsfeed 确实没一手经验只能答案八股🤷所以就是人有选择的时候还是去小公司试试看也挺好的，真的造小火箭的几率比大公司虽然有大火箭但你只能拧螺丝还是高多了

祝大家找到又喜欢钱又多的工作！（应该没有不找工作的人会看完一篇八千多字还大多数是英文看到这儿的中文读者吧……）
<!-- 恢复评论 -->