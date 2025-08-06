# 🛠️ 50-Day System Design Learning Plan

**Goal**: Learn high-level system design by building real-world scalable applications.

**Note** I'm creating this repo for learning how to write technical things, improve my consistency in learning, and to help someone in case they try to learn SD! Currently the plan is for 50 days these problems, but I might keep adding more things over here if I'll enjoy this series

---

## 📅 Week 1: Fundamentals & Basic Systems

### Day 1: URL Shortener
- Concepts: Hashing, Read-heavy optimisation, Base62 encoding
- Scale: Millions of reads, few writes

### Day 2: Pastebin
- Concepts: Expiry TTL, CDN, Rate limiting
- Bonus: Abuse prevention

### Day 3: Rate Limiter
- Concepts: Sliding Window, Token Bucket, Redis, Middleware in Go/TS

### Day 4: Design YouTube Comments
- Concepts: Tree data structure, Pagination, Soft delete

### Day 5: Real-time Chat App
- Concepts: WebSockets, Redis pub/sub, Message queues

### Day 6–7: Instagram Backend (2-day project)
- Concepts: Image processing, Feed generation, Followers graph
- Scale: Billions of photos

---

## 📅 Week 2: Intermediate Complexity

### Day 8: News Feed (Facebook/Twitter)
- Concepts: Pull vs Push model, Fan-out on write/read

### Day 9: Design a Job Scheduler (like cron)
- Concepts: Priority queues, Workers, Retry logic, Failover

### Day 10: Notification System
- Concepts: Fan-out, Retry, Dead-letter queues, Delay queues

### Day 11: Designing an Email System
- Concepts: SMTP integration, Idempotency, Logging

### Day 12: WhatsApp-like Chat
- Concepts: Message sync, Offline queueing, Acks, Encryption basics

### Day 13–14: Google Docs Clone (Real-time Editor)
- Concepts: CRDT, Operational Transform, WebSockets, OT vs CRDT

---

## 📅 Week 3: Storage Systems and Databases

### Day 15: File Storage System (S3 clone)
- Concepts: Chunking, Metadata, CDN, Data replication

### Day 16: Key-Value Store
- Concepts: LSM trees, Memtables, Compaction, Persistence

### Day 17: Log Aggregator System
- Concepts: Kafka-like systems, Backpressure, Partitioning

### Day 18: Design a Time Series DB (like Prometheus)
- Concepts: Compression, Bucketing, Query engine

### Day 19: E-commerce Checkout Flow
- Concepts: Consistency, Inventory locking, Atomicity

### Day 20–21: Netflix Backend (2-day project)
- Concepts: CDN, Encoding, Rate control, Metadata search

---

## 📅 Week 4: Advanced Scenarios

### Day 22: Collaborative Whiteboard App
- Concepts: Real-time sync, Cursors, OT/CRDT

### Day 23: Notification Feed (Like LinkedIn)
- Concepts: Ranking, Read Receipts, Visibility

### Day 24: Design a Parking Lot System
- Concepts: Object-Oriented Design, Real-world constraints

### Day 25: Online IDE
- Concepts: Code Execution Sandbox, Queuing, Real-time collaboration

### Day 26: Online Judge System (like LeetCode)
- Concepts: Worker pool, Time limits, Sandboxed environments

### Day 27–28: Ride Sharing App (Uber clone)
- Concepts: Geo-indexing, Real-time matching, Surge pricing

---

## 📅 Week 5: Distributed Systems & Scaling

### Day 29: Distributed Lock Service
- Concepts: Paxos/Raft basics, Leader Election, Zookeeper

### Day 30: API Gateway Design
- Concepts: Rate limit, Circuit breaker, Aggregation

### Day 31: Search Service (like Elastic)
- Concepts: Inverted index, Ranking, Caching

### Day 32: Caching Layer (like Redis)
- Concepts: Write-through, Write-back, Eviction policies

### Day 33: Message Broker System
- Concepts: Pub/Sub, Acknowledgments, Retention

### Day 34–35: Kubernetes Scheduler Design
- Concepts: Resource allocation, Bin packing, Failover

---

## 📅 Week 6: Finishing Strong

### Day 36: Analytics Dashboard (Mixpanel-style)
- Concepts: Aggregation, OLAP vs OLTP, Rollups

### Day 37: CRM Tool Backend
- Concepts: Multi-tenancy, Role-based access control

### Day 38: SaaS Billing System
- Concepts: Stripe integration, Webhooks, Metered billing

### Day 39: Feature Flag System
- Concepts: Rollouts, AB Testing, Config services

### Day 40: Low-Level Design - Auth System
- Concepts: OAuth, SSO, JWT, Sessions, 2FA

### Day 41–42: YouTube Scale System Design (2-day)
- Revisit and scale: Thumbnails, Metadata, Transcoding, Live Streaming

### Day 43: Ads Delivery System
- Concepts: Budgeting, Relevance, Real-time bidding (RTB)

### Day 44: Web Crawler
- Concepts: BFS, Throttling, Robots.txt, Indexing

### Day 45: Blockchain Simplified
- Concepts: Hashing, Merkle trees, Proof-of-work

### Day 46: Git Internals
- Concepts: Trees, Blobs, Commits, Refs

### Day 47: DNS Resolver
- Concepts: Caching, Recursion, Root servers

### Day 48: Load Balancer
- Concepts: Round robin, IP hash, Health checks

### Day 49: CDN Design
- Concepts: Edge nodes, Consistency, Cache invalidation

### Day 50: System Design Interview Day
- Simulate 1 interview end-to-end (record or write up)
- Review learnings

Let me know if you want a printable `.pdf` version as well or want to update the plan later.

