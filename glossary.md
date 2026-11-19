# Glossary & Acronyms (SAA-C03)

## Core acronyms
| Acronym | Meaning |
|---------|---------|
| AZ | Availability Zone (isolated datacenter(s) within a Region) |
| Region | Geographic area containing multiple AZs |
| VPC | Virtual Private Cloud |
| IGW | Internet Gateway |
| NAT | Network Address Translation (NAT Gateway) |
| SG | Security Group (stateful, instance-level) |
| NACL | Network ACL (stateless, subnet-level) |
| CIDR | Classless Inter-Domain Routing (IP range notation) |
| ENI | Elastic Network Interface |
| EIP | Elastic IP (static public IP) |

## Compute
| Acronym | Meaning |
|---------|---------|
| EC2 | Elastic Compute Cloud (virtual servers) |
| AMI | Amazon Machine Image |
| ASG | Auto Scaling Group |
| ELB / ALB / NLB / GWLB | Elastic Load Balancer / Application / Network / Gateway |
| ECS / EKS | Elastic Container Service / Elastic Kubernetes Service |
| ECR | Elastic Container Registry |
| RI | Reserved Instance |

## Storage
| Acronym | Meaning |
|---------|---------|
| S3 | Simple Storage Service (object storage) |
| EBS | Elastic Block Store |
| EFS | Elastic File System |
| FSx | Managed file systems (Windows, Lustre, etc.) |
| IA | Infrequent Access (storage class) |
| CRR / SRR | Cross-Region / Same-Region Replication |
| SSE | Server-Side Encryption (SSE-S3, SSE-KMS, SSE-C) |
| WORM | Write Once Read Many (Object Lock) |

## Databases
| Acronym | Meaning |
|---------|---------|
| RDS | Relational Database Service |
| DAX | DynamoDB Accelerator (in-memory cache) |
| OLTP / OLAP | Transaction processing / Analytical processing |
| TTL | Time To Live (auto-expire items) |
| GSI / LSI | Global / Local Secondary Index |

## Security & identity
| Acronym | Meaning |
|---------|---------|
| IAM | Identity and Access Management |
| STS | Security Token Service (temporary credentials) |
| KMS | Key Management Service |
| HSM | Hardware Security Module (CloudHSM) |
| ACM | AWS Certificate Manager |
| MFA | Multi-Factor Authentication |
| SCP | Service Control Policy (Organizations) |
| WAF | Web Application Firewall |
| SSO | Single Sign-On (IAM Identity Center) |

## Integration & analytics
| Acronym | Meaning |
|---------|---------|
| SQS | Simple Queue Service |
| SNS | Simple Notification Service |
| DLQ | Dead-Letter Queue |
| FIFO | First-In-First-Out (ordered, exactly-once) |
| ETL | Extract, Transform, Load |
| MSK | Managed Streaming for Apache Kafka |

## Resilience / DR
| Term | Meaning |
|------|---------|
| HA | High Availability (fast recovery) |
| Fault tolerant | Keeps running through failure, no interruption |
| Durability | Probability data is not lost (S3 = 11 nines) |
| RTO | Recovery Time Objective (how fast you recover) |
| RPO | Recovery Point Objective (how much data loss is acceptable) |
| Multi-AZ | Deployment across ≥2 Availability Zones |

## Billing / cost
| Term | Meaning |
|------|---------|
| Savings Plan | Commitment-based discount, flexible |
| Spot | Spare capacity, up to 90% off, interruptible |
| On-Demand | Pay-as-you-go, no commitment |
| Consolidated billing | One bill across Organization accounts |

## Durability "nines" quick note
- S3 Standard durability = 99.999999999% (11 nines).
- Availability targets differ by storage class (e.g., Standard 99.99%, One Zone-IA lower).
