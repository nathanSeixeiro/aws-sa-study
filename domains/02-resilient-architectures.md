# Domain 2: Design Resilient Architectures (26%)

## Task statements
1. Design scalable and loosely coupled architectures
2. Design highly available and/or fault-tolerant architectures

---

## 1. Key resilience vocabulary

- **High Availability (HA)** — system recovers quickly from failure (minimal downtime). Usually Multi-AZ.
- **Fault tolerance** — system keeps running through failure with no interruption. Stronger/pricier.
- **Durability** — data won't be lost (e.g., S3 = 11 nines, 99.999999999%).
- **Scalability** — handle more load. *Horizontal* (add instances) usually beats *vertical* (bigger instance) for resilience.
- **RTO** (Recovery Time Objective) — how fast you must recover. **RPO** (Recovery Point Objective) — how much data loss is acceptable.

## 2. Decoupling / loose coupling

- **SQS** — durable message **queue**; one message consumed by one worker. Absorbs spikes, retains messages if consumer is down. Standard (at-least-once, best-effort order) vs FIFO (exactly-once, ordered).
- **SNS** — pub/sub **fan-out**; one message to many subscribers (SQS, Lambda, HTTP, email).
- **SQS + SNS fan-out pattern** — SNS topic delivers to multiple SQS queues.
- **EventBridge** — event bus routing events between AWS services and SaaS; rich filtering.
- **Step Functions** — orchestrate multi-step workflows with state, retries, error handling.
- **API Gateway** — front doors for APIs; throttling, caching.

## 3. High availability building blocks

- **Multi-AZ** — deploy across ≥2 Availability Zones. The foundation of HA on AWS.
- **Elastic Load Balancing (ELB)** — spreads traffic across healthy targets in multiple AZs.
  - ALB (layer 7, HTTP/HTTPS, path/host routing), NLB (layer 4, ultra-high performance, static IP), GWLB (appliances).
- **Auto Scaling Groups (ASG)** — maintain desired capacity, replace unhealthy instances, scale on demand. Use health checks + multiple AZs.
- **Route 53** routing policies: simple, weighted, latency, failover, geolocation, geoproximity, multivalue. Health checks enable DNS failover.

## 4. Database resilience

- **RDS Multi-AZ** — synchronous standby in another AZ, **automatic failover**, same endpoint. For *availability*, NOT read scaling.
- **RDS Read Replicas** — asynchronous copies for **read scaling**; can be promoted manually. Not automatic failover.
- **Aurora** — storage replicated 6 ways across 3 AZs; auto-healing; up to 15 read replicas; Aurora Global Database for cross-Region DR.
- **DynamoDB** — multi-AZ by default; Global Tables for multi-Region active-active.

## 5. Durable storage & backups

- **S3** — 11 nines durability; versioning; Cross-Region Replication (CRR) and Same-Region Replication (SRR).
- **EBS snapshots** — point-in-time backups stored in S3; can copy across Regions.
- **AWS Backup** — centralized backup across services.

## 6. Disaster recovery strategies (cheapest/slowest → priciest/fastest)
1. **Backup & Restore** — restore from backups after disaster. High RTO/RPO, low cost.
2. **Pilot Light** — core minimal services always on, scale up on failover.
3. **Warm Standby** — scaled-down full copy always running, scale up on failover.
4. **Multi-Site Active/Active** — full capacity in multiple Regions. Lowest RTO/RPO, highest cost.

---

## Decision cues
| If the question says... | Think... |
|-------------------------|----------|
| "decouple / absorb spikes / don't lose work" | SQS queue |
| "notify many subscribers at once" | SNS fan-out |
| "automatic DB failover, no code change" | RDS Multi-AZ |
| "scale read traffic on the database" | Read Replicas (or DynamoDB/Aurora) |
| "survive the loss of an Availability Zone" | Multi-AZ + ELB + ASG |
| "active-active across Regions for DynamoDB" | Global Tables |
| "cheapest DR, can tolerate long recovery" | Backup & Restore |
| "near-zero downtime DR" | Multi-site active/active |

## Common exam traps
- Multi-AZ = availability; Read Replicas = read scaling. Don't swap them.
- "Fault tolerant" (no interruption) is a stronger requirement than "highly available."
- SQS buffers and retains; an ALB does not buffer requests.
- Stateless app tiers (store session in DynamoDB/ElastiCache) are what make Auto Scaling safe.

## My notes
<!-- fill in as you study -->
