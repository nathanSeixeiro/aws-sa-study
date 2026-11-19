# Practice Set 03 — SAA-C03 (Storage, Databases, Performance, Cost)

8 questions. Answer all before scrolling to the key.

---

## Q1 — Storage / Cost
Logs are accessed frequently for 30 days, rarely afterward, and must be kept 7 years for
compliance at the lowest cost. What is the BEST approach?

- A. Keep everything in S3 Standard forever
- B. S3 Lifecycle rule: Standard → Standard-IA after 30 days → Glacier Deep Archive, with 7-year expiration
- C. Store in EBS volumes and snapshot monthly
- D. Delete logs after 30 days

## Q2 — Database / Performance
A DynamoDB-backed app needs microsecond read latency during spikes, with no changes to the
application's data model or API calls. What should be added?

- A. An RDS Read Replica
- B. DynamoDB Accelerator (DAX)
- C. Amazon Redshift
- D. S3 Transfer Acceleration

## Q3 — Database / Availability
A MySQL RDS database must fail over automatically to another AZ with no application changes.
Which feature meets this?

- A. Read Replica in another Region
- B. RDS Multi-AZ deployment
- C. Manual snapshot restore
- D. DynamoDB Global Tables

## Q4 — Storage
Several hundred Linux EC2 instances across multiple AZs must share the same file system with
read/write access. Which service fits?

- A. Amazon EBS
- B. Amazon EFS
- C. Instance store
- D. Amazon FSx for Windows File Server

## Q5 — Cost / Storage
A company cannot predict access patterns for a large, growing S3 dataset and wants to minimize
cost without manual tuning. Which storage class is BEST?

- A. S3 Standard
- B. S3 One Zone-IA
- C. S3 Intelligent-Tiering
- D. S3 Glacier Deep Archive

## Q6 — Resilience / Decoupling
Order spikes overwhelm a backend and orders are lost when it's briefly down. The team wants to
decouple so spikes are absorbed and no orders are lost. What should they use?

- A. Amazon SQS queue the backend polls
- B. Application Load Balancer
- C. Amazon SNS email subscription
- D. Amazon ElastiCache

## Q7 — Database / Analytics
An analytics team needs to run complex SQL queries over petabytes of historical data for
reporting (OLAP). Which service is designed for this?

- A. Amazon DynamoDB
- B. Amazon RDS for MySQL
- C. Amazon Redshift
- D. Amazon ElastiCache

## Q8 — Performance / Cost
An EBS-backed database needs high, consistent IOPS, and the team wants to provision IOPS and
throughput independently of volume size at the best price. Which volume type?

- A. gp2
- B. gp3
- C. sc1
- D. st1

---
---

## Answer key

**Q1 — B.** Lifecycle rule transitioning to cheaper tiers then archiving to Glacier Deep Archive,
with expiration at 7 years, minimizes cost while meeting retention. *Domain 4, Cost.*

**Q2 — B.** DAX adds microsecond in-memory reads for DynamoDB, API-compatible, no data-model
change. *Domain 3, Performance.*

**Q3 — B.** RDS Multi-AZ provides automatic failover to a standby in another AZ via the same
endpoint, no app changes. *Domain 2, Resilience.*

**Q4 — B.** EFS is shared NFS for many Linux instances across AZs. EBS is single-instance;
instance store is ephemeral; FSx for Windows is SMB/Windows. *Domain 3, Storage.*

**Q5 — C.** S3 Intelligent-Tiering auto-moves objects between tiers for unknown/changing access
with no manual tuning. *Domain 4, Cost.*

**Q6 — A.** SQS decouples and buffers, retaining messages if the backend is down, so no orders are
lost. ALB doesn't buffer; SNS is fan-out; ElastiCache isn't a durable queue. *Domain 2.*

**Q7 — C.** Redshift is the columnar data warehouse built for OLAP over huge datasets. DynamoDB/RDS
are OLTP; ElastiCache is caching. *Domain 3, Databases.*

**Q8 — B.** gp3 lets you provision IOPS and throughput independently of size at a better price than
gp2 for many workloads. *Domain 3/4.*
