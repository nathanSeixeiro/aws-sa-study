# Domain 4: Design Cost-Optimized Architectures (20%)

## Task statements
1. Design cost-optimized storage solutions
2. Design cost-optimized compute solutions
3. Design cost-optimized database solutions
4. Design cost-optimized network architectures

---

## 1. Compute cost levers

| Option | Discount | Best for |
|--------|----------|----------|
| On-Demand | none | Short-term, unpredictable, spiky |
| Savings Plans | up to ~72% | Steady usage, flexible across instance families/Lambda/Fargate |
| Reserved Instances | up to ~72% | Steady, predictable, specific instance type |
| Spot Instances | up to ~90% | Fault-tolerant, interruptible, stateless, batch |
| Dedicated Hosts | premium | Licensing/compliance requiring physical isolation |

- **Serverless (Lambda/Fargate)** — pay per use, no idle cost; great for spiky/low-traffic.
- **Auto Scaling** — scale in during low demand so you don't pay for idle capacity.
- **Right-sizing** — use AWS Compute Optimizer to match instance size to actual load.

## 2. Storage cost levers

- **S3 storage classes** (frequent → archive):
  - S3 Standard → Standard-IA → One Zone-IA → Glacier Instant Retrieval → Glacier Flexible Retrieval → Glacier Deep Archive.
  - **Intelligent-Tiering** — auto-moves objects between tiers when access patterns are unknown/changing. Pick this when you can't predict access.
- **S3 Lifecycle rules** — transition objects to cheaper classes and expire them automatically.
- **EBS** — delete unattached volumes; snapshot + delete idle volumes; use gp3 (cheaper than gp2 for many workloads).
- **EFS Infrequent Access** + lifecycle management for shared files.

## 3. Database cost levers

- **RDS**: Reserved Instances for steady DBs; stop dev/test DBs when idle; right-size.
- **Aurora Serverless v2** — scales capacity automatically for variable/intermittent load; avoids paying for peak 24/7.
- **DynamoDB**: On-demand (unpredictable) vs Provisioned + Auto Scaling (predictable, cheaper at steady scale). Use TTL to auto-expire old items.

## 4. Network cost levers

- **Data transfer**: inbound is usually free; **outbound to internet costs**; cross-AZ and cross-Region transfer costs. Keep traffic local where possible.
- **VPC endpoints** — avoid NAT Gateway/data-transfer charges for S3/DynamoDB (Gateway endpoints are free).
- **NAT Gateway** — charged per hour + per GB; consolidate; consider endpoints to reduce usage.
- **CloudFront** — can lower origin data-transfer costs by caching at the edge.

## 5. Cost visibility & governance

- **Cost Explorer** — analyze and forecast spend.
- **AWS Budgets** — alerts when spend/usage crosses thresholds.
- **Cost allocation tags** — attribute costs to teams/projects.
- **AWS Organizations consolidated billing** — volume discounts + shared RIs/Savings Plans across accounts.
- **Trusted Advisor** — cost optimization checks (idle resources, underutilized instances).

---

## Decision cues
| If the question says... | Think... |
|-------------------------|----------|
| "interruptible / fault-tolerant batch, cheapest compute" | Spot Instances |
| "steady predictable usage, lower compute cost" | Savings Plans / Reserved Instances |
| "unknown or changing S3 access pattern" | S3 Intelligent-Tiering |
| "automatically move old data to cheaper storage" | S3 Lifecycle rules |
| "variable/intermittent database load, don't pay for peak" | Aurora Serverless v2 |
| "reduce NAT/data-transfer cost for S3 access" | S3 Gateway VPC endpoint |
| "get alerted when spend exceeds a limit" | AWS Budgets |

## Common exam traps
- Spot = cheapest but can be reclaimed; never for stateful/critical always-on work.
- Intelligent-Tiering when access is *unpredictable*; manual Lifecycle when you *know* the pattern.
- Gateway endpoints (S3, DynamoDB) are free and cut data-transfer/NAT costs.
- Cheapest answer isn't always correct — it must still meet the stated requirement.

## My notes
<!-- fill in as you study -->
