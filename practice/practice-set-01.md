# Practice Set 01 — SAA-C03

5 questions, one per answer-and-explanation at the bottom. Try all 5 before scrolling to the key.
Covers all four domains. Format matches the real exam (multiple choice, one best answer).

---

## Q1 — Domain 1: Secure Architectures
An application running on an EC2 instance needs to read objects from an S3 bucket. The
security team requires that no long-term credentials be stored on the instance. What is the
MOST secure way to grant the access?

- A. Create an IAM user, generate an access key, and store it in a file on the instance
- B. Attach an IAM role with an S3 read policy to the EC2 instance
- C. Hard-code the AWS account root credentials in the application config
- D. Store an access key in an environment variable on the instance

---

## Q2 — Domain 2: Resilient Architectures
A company runs a MySQL database on Amazon RDS. They need automatic failover to a standby
in another Availability Zone if the primary fails, with no application code changes. Which
feature meets this requirement?

- A. RDS Read Replicas
- B. RDS Multi-AZ deployment
- C. Copying automated snapshots to another Region
- D. Enabling S3 Cross-Region Replication

---

## Q3 — Domain 3: High-Performing Architectures
A read-heavy web application uses Amazon DynamoDB. During traffic spikes, read latency
increases and some requests are throttled. The team wants microsecond read latency without
changing the data model. What should they add?

- A. Amazon ElastiCache for Memcached in front of the application tier
- B. Amazon DynamoDB Accelerator (DAX)
- C. An RDS Read Replica
- D. Amazon S3 Transfer Acceleration

---

## Q4 — Domain 4: Cost-Optimized Architectures
A company runs a nightly batch job on EC2 that can tolerate interruption and be restarted at
any time. They want to minimize compute cost. Which purchasing option is BEST?

- A. On-Demand Instances
- B. Reserved Instances (1-year, all upfront)
- C. Spot Instances
- D. Dedicated Hosts

---

## Q5 — Domain 1 + 2: Decoupling & Resilience
A web tier writes orders directly to a backend processing tier. During sales events the backend
is overwhelmed and orders are lost. The team wants to decouple the tiers so spikes are absorbed
and no orders are lost if the backend is briefly down. What should they use?

- A. Place an Application Load Balancer between the tiers
- B. Send orders to an Amazon SQS queue that the backend polls
- C. Publish orders to an Amazon SNS topic the backend subscribes to with email
- D. Store orders in ElastiCache and have the backend read them

---
---

## Answer key (no peeking until you've answered all 5)

**Q1 — B.** Attach an IAM role to the instance. Roles provide temporary, automatically rotated
credentials so no long-term keys live on the instance. A, C, D all store long-lived secrets (and
root credentials should never be used). *Domain 1: Design Secure Architectures.*

**Q2 — B.** RDS Multi-AZ keeps a synchronous standby in another AZ and fails over automatically
via the same DNS endpoint, so no app changes are needed. Read Replicas scale reads but are async
and not automatic failover. *Domain 2: Design Resilient Architectures.*

**Q3 — B.** DAX is a purpose-built, in-memory cache for DynamoDB that delivers microsecond reads
with no data-model or API changes (it's DynamoDB-API compatible). ElastiCache would require app
changes; RDS and S3 options are unrelated. *Domain 3: Design High-Performing Architectures.*

**Q4 — C.** Spot Instances offer the deepest discount and suit interruptible, restartable batch
work. Reserved Instances fit steady, always-on workloads; On-Demand and Dedicated Hosts cost more.
*Domain 4: Design Cost-Optimized Architectures.*

**Q5 — B.** An SQS queue decouples the tiers, buffers spikes, and retains messages if the backend
is down, so no orders are lost. An ALB doesn't buffer. SNS is fan-out, not durable work queuing for
one consumer. ElastiCache isn't a durable queue. *Domains 1 & 2: decoupling + resilience.*

**Score yourself:** 4-5 correct = strong; 3 = review the missed domains; 0-2 = re-read the domain
files and retry. Log results in `question-log.md` and move misses to `notes/weak-spots.md`.
