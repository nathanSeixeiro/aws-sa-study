# Domain 3: Design High-Performing Architectures (24%)

## Task statements
1. Determine high-performing and/or scalable storage solutions
2. Design high-performing and elastic compute solutions
3. Determine high-performing database solutions
4. Determine high-performing and/or scalable network architectures
5. Determine high-performing data ingestion and transformation solutions

---

## 1. High-performing compute

- **EC2 families**: General purpose (M, T), Compute optimized (C), Memory optimized (R, X), Storage optimized (I, D), Accelerated (P, G — GPU/ML).
- **Auto Scaling** — scale out horizontally; target tracking, step, scheduled policies.
- **Lambda** — serverless, scales automatically per request; good for event-driven/spiky workloads; watch memory→CPU coupling and timeout limits.
- **Containers** — ECS (AWS-native), EKS (Kubernetes), Fargate (serverless containers, no node management).
- **Placement groups**: Cluster (low latency, same AZ), Spread (separate hardware), Partition (large distributed systems).

## 2. High-performing storage

- **EBS volume types**: gp3 (general SSD, provision IOPS/throughput independently — usually best default), io1/io2 (high IOPS, mission-critical DBs), st1 (throughput HDD), sc1 (cold HDD).
- **Instance store** — ephemeral, very high IOPS, lost on stop/terminate.
- **EFS** — elastic shared NFS for many Linux instances; scales automatically.
- **FSx** — FSx for Windows (SMB), FSx for Lustre (HPC/ML, integrates with S3).
- **S3 performance** — 3,500 PUT / 5,500 GET per prefix per second; use multiple prefixes to parallelize; S3 Transfer Acceleration for fast long-distance uploads; multipart upload for large objects.

## 3. High-performing databases

- **RDS / Aurora** — relational; Aurora is faster + auto-scaling storage; Aurora Serverless v2 for variable load.
- **DynamoDB** — single-digit ms at any scale; **DAX** adds microsecond reads (in-memory, DynamoDB-API compatible, no code change). On-demand vs provisioned capacity; adaptive capacity; Global Secondary Indexes.
- **ElastiCache** — Redis (persistence, replication, pub/sub, sorted sets) vs Memcached (simple, multi-threaded, no persistence). Use for session stores, leaderboards, DB read offload.
- **Redshift** — columnar data warehouse for analytics; Redshift Spectrum queries S3 directly.

## 4. High-performing networking & delivery

- **CloudFront** — CDN caches content at edge locations near users; lowers latency; origin can be S3/ALB/custom.
- **Global Accelerator** — static anycast IPs + AWS backbone routing for non-HTTP/global TCP/UDP apps.
- **Enhanced networking / ENA / placement groups** — for high throughput, low latency between instances.
- **VPC peering / Transit Gateway** — connect VPCs; Transit Gateway scales to many VPCs/accounts.
- **Direct Connect** — dedicated private link to AWS (consistent performance vs VPN over internet).

## 5. Data ingestion & processing

- **Kinesis Data Streams** — real-time streaming ingestion (shards).
- **Kinesis Data Firehose** — load streaming data to S3/Redshift/OpenSearch, near-real-time.
- **Amazon MSK** — managed Kafka.
- **AWS Glue** — serverless ETL + data catalog.
- **Amazon Athena** — serverless SQL queries directly on S3.
- **EMR** — managed big-data (Spark/Hadoop).

---

## Decision cues
| If the question says... | Think... |
|-------------------------|----------|
| "microsecond reads for DynamoDB, no code change" | DAX |
| "cache DB reads / session store / leaderboard" | ElastiCache (Redis) |
| "deliver content with low latency worldwide" | CloudFront |
| "static IP + AWS backbone for a TCP/UDP app" | Global Accelerator |
| "shared file system across many Linux instances" | EFS |
| "query data directly in S3 with SQL, no servers" | Athena |
| "real-time streaming ingestion" | Kinesis Data Streams |
| "provision IOPS independent of volume size" | gp3 (or io2) |

## Common exam traps
- DAX is specifically for DynamoDB; ElastiCache is general-purpose caching.
- CloudFront = HTTP content delivery/caching; Global Accelerator = network-layer routing for any protocol.
- gp3 decouples IOPS/throughput from size; gp2's performance scales with size.
- Athena queries S3 directly (no loading); Redshift needs data loaded (or Spectrum).

## My notes
<!-- fill in as you study -->
