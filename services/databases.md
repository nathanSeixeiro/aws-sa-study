# Database Services (SAA-C03)

## RDS (managed relational)
- Engines: MySQL, PostgreSQL, MariaDB, Oracle, SQL Server.
- **Multi-AZ** — synchronous standby, automatic failover (availability, NOT read scaling).
- **Read Replicas** — async, read scaling, can be cross-Region, promotable.
- Automated backups + snapshots; encryption with KMS.
- Use for traditional SQL workloads needing managed HA.

## Aurora (AWS-built relational)
- MySQL/PostgreSQL compatible; ~5x/3x faster.
- Storage auto-scales, replicated 6 ways across 3 AZs, self-healing.
- Up to 15 read replicas; fast failover.
- **Aurora Serverless v2** — auto-scales capacity for variable load.
- **Aurora Global Database** — cross-Region, low-latency reads + DR.

## DynamoDB (managed NoSQL)
- Key-value / document; single-digit ms at any scale; fully serverless.
- Capacity: on-demand (unpredictable) vs provisioned + auto scaling (steady).
- **DAX** — in-memory cache, microsecond reads, no code change.
- **Global Tables** — multi-Region active-active.
- **Streams** — change data capture (trigger Lambda).
- **TTL** — auto-expire items.
- GS/LSI indexes for alternate query patterns.

## ElastiCache (in-memory)
- **Redis** — persistence, replication, pub/sub, sorted sets, Multi-AZ.
- **Memcached** — simple, multi-threaded, no persistence.
- Use for session stores, leaderboards, caching DB reads.

## Redshift (data warehouse)
- Columnar, petabyte-scale analytics (OLAP).
- Redshift Spectrum queries S3 directly.
- Not for transactional (OLTP) workloads.

## Other
- **Neptune** — graph database.
- **DocumentDB** — MongoDB-compatible.
- **Keyspaces** — Cassandra-compatible.
- **Timestream** — time-series.
- **QLDB** — ledger (immutable).

## Pick-the-right-database
| Need | Pick |
|------|------|
| Traditional SQL, managed HA | RDS Multi-AZ |
| High-performance relational + DR | Aurora |
| Massive scale key-value, serverless | DynamoDB |
| Microsecond cached reads for DynamoDB | DAX |
| Session store / cache / leaderboard | ElastiCache (Redis) |
| Analytics over huge datasets | Redshift |
| Relationships / graph queries | Neptune |

## Traps
- OLTP (transactions) → RDS/Aurora/DynamoDB. OLAP (analytics) → Redshift.
- Multi-AZ ≠ Read Replica (availability vs read scaling).
- DAX is DynamoDB-specific; ElastiCache is general.
