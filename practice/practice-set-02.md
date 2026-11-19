# Practice Set 02 — SAA-C03 (Networking, Compute, Security)

7 questions. Answer all before scrolling to the key at the bottom.

---

## Q1 — Networking
Instances in a private subnet need to download OS patches from the internet but must not be
reachable from the internet. What should you deploy?

- A. An Internet Gateway attached to the private subnet
- B. A NAT Gateway in a public subnet, with a route from the private subnet to it
- C. A VPC peering connection to a public VPC
- D. An Elastic IP on each private instance

## Q2 — Security
A compliance rule requires that an audit trail of every AWS API call in the account be retained.
Which service provides this?

- A. Amazon CloudWatch
- B. AWS Config
- C. AWS CloudTrail
- D. Amazon GuardDuty

## Q3 — Compute / Cost
A stateless image-processing workload runs in batches and can be safely restarted if interrupted.
The team wants the lowest possible compute cost. What should they use?

- A. On-Demand EC2 instances
- B. Spot Instances in an Auto Scaling group
- C. Dedicated Hosts
- D. Reserved Instances

## Q4 — Networking / Delivery
A global audience streams video and experiences high latency fetching static assets stored in a
single S3 bucket. What improves performance MOST?

- A. Enable S3 Versioning
- B. Put Amazon CloudFront in front of the S3 bucket
- C. Switch the bucket to S3 One Zone-IA
- D. Enable S3 Transfer Acceleration for downloads

## Q5 — Security / Network
A web application must block common SQL injection and cross-site scripting attacks at the
application layer. Which service should be attached?

- A. Security Groups
- B. Network ACLs
- C. AWS WAF
- D. Amazon GuardDuty

## Q6 — Compute / Availability
A web tier must stay available even if an entire Availability Zone fails, and automatically
adjust capacity to load. Which combination is BEST?

- A. A single large EC2 instance with a larger instance type
- B. EC2 instances in one AZ behind an ALB
- C. An Auto Scaling group across multiple AZs behind an ALB
- D. A NAT Gateway in front of the EC2 instances

## Q7 — Security / Secrets
An application needs database credentials that are rotated automatically every 30 days with no
code changes to fetch the latest value. What should be used?

- A. Hard-code credentials in the application
- B. AWS Secrets Manager with automatic rotation
- C. Store credentials in an S3 bucket
- D. SSM Parameter Store String parameter (plaintext)

---
---

## Answer key

**Q1 — B.** NAT Gateway in a public subnet gives private instances outbound internet while
blocking inbound. IGW would expose them; EIP makes them reachable. *Domain 1/2, networking.*

**Q2 — C.** CloudTrail records API calls (the audit trail). Config tracks resource config/compliance;
CloudWatch is metrics/logs; GuardDuty is threat detection. *Domain 1, Security.*

**Q3 — B.** Spot Instances give the deepest discount and fit interruptible, restartable, stateless
batch work; run them in an ASG. *Domain 4, Cost.*

**Q4 — B.** CloudFront caches static assets at edge locations near users, cutting latency globally.
Transfer Acceleration helps uploads more than general global reads; versioning/One Zone-IA don't
address latency. *Domain 3, Performance.*

**Q5 — C.** AWS WAF filters layer-7 attacks like SQLi and XSS. SG/NACL operate at network layers;
GuardDuty detects, it doesn't block inline. *Domain 1, Security.*

**Q6 — C.** ASG across multiple AZs behind an ALB gives both AZ-failure resilience and elastic
capacity. A single instance or single-AZ setup fails the requirement. *Domain 2, Resilience.*

**Q7 — B.** Secrets Manager stores secrets and rotates them automatically (native RDS integration);
the app fetches the current value at runtime. Plaintext/hard-coded options are insecure. *Domain 1.*
