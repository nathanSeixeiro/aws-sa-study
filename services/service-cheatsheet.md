# SAA-C03 Service Cheatsheet

Quick "what it is + when to pick it" reference. Expand as you study.

## Storage
| Service | What it is | Pick it when |
|---------|-----------|--------------|
| S3 | Object storage | Files, backups, static sites, data lakes |
| EBS | Block storage for EC2 | Single-instance disk, databases on EC2 |
| EFS | Managed NFS file storage | Shared file system across many Linux instances |
| FSx | Managed Windows/Lustre FS | Windows shares, HPC workloads |
| Glacier | Archival object storage | Long-term, rarely accessed, cheapest |

## Compute
| Service | What it is | Pick it when |
|---------|-----------|--------------|
| EC2 | Virtual servers | Full control over OS/runtime |
| Lambda | Serverless functions | Event-driven, spiky, no server mgmt |
| ECS/EKS | Container orchestration | Containerized apps |
| Fargate | Serverless containers | Containers without managing nodes |

## Databases
| Service | What it is | Pick it when |
|---------|-----------|--------------|
| RDS | Managed relational DB | SQL, Multi-AZ HA, read replicas |
| Aurora | AWS-built relational | High-performance MySQL/Postgres compatible |
| DynamoDB | Managed NoSQL | Key-value, single-digit ms at scale |
| ElastiCache | In-memory cache | Sub-ms reads, session store |
| Redshift | Data warehouse | Analytics over large datasets |

## Networking & delivery
| Service | What it is | Pick it when |
|---------|-----------|--------------|
| VPC | Virtual network | Isolate and control your network |
| Route 53 | DNS + routing policies | DNS, failover, latency routing |
| CloudFront | CDN | Cache content near users, lower latency |
| ELB | Load balancer | Distribute traffic, HA across AZs |

## Integration / decoupling
| Service | What it is | Pick it when |
|---------|-----------|--------------|
| SQS | Message queue | Decouple producers/consumers, absorb spikes |
| SNS | Pub/sub notifications | Fan-out to many subscribers |
| EventBridge | Event bus | Route events between services/SaaS |
