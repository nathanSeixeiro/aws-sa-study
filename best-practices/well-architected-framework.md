# AWS Well-Architected Framework

The SAA-C03 exam is built around the Well-Architected Framework. Nearly every question is
really asking: "which pillar does this requirement serve, and which service/design satisfies it?"

## The 6 Pillars

### 1. Operational Excellence
Run and monitor systems, continuously improve processes.
- Design principles: perform operations as code (IaC), make frequent small reversible changes, anticipate failure, learn from failures.
- Key services: CloudFormation, CloudWatch, CloudTrail, Systems Manager, AWS Config.

### 2. Security
Protect data, systems, and assets.
- Design principles: strong identity foundation (least privilege), enable traceability, apply security at all layers, protect data in transit and at rest, keep people away from data, prepare for security events.
- Key services: IAM, KMS, WAF, Shield, GuardDuty, Macie, Secrets Manager, CloudTrail.

### 3. Reliability
Recover from failure, scale to meet demand.
- Design principles: automatically recover from failure, test recovery procedures, scale horizontally, stop guessing capacity, manage change through automation.
- Key services: Multi-AZ, Auto Scaling, ELB, Route 53, SQS, RDS Multi-AZ, AWS Backup.

### 4. Performance Efficiency
Use resources efficiently; pick the right tool.
- Design principles: democratize advanced tech (use managed services), go global in minutes, use serverless, experiment often, mechanical sympathy (match tech to workload).
- Key services: Auto Scaling, Lambda, CloudFront, DAX, ElastiCache, right instance families.

### 5. Cost Optimization
Avoid unnecessary cost.
- Design principles: adopt consumption model, measure efficiency, stop spending on undifferentiated heavy lifting (data center ops), analyze/attribute expenditure.
- Key services: Spot, Savings Plans/RIs, S3 lifecycle + Intelligent-Tiering, Cost Explorer, Budgets, Trusted Advisor.

### 6. Sustainability
Minimize environmental impact.
- Design principles: maximize utilization, use managed services, reduce downstream impact, adopt efficient hardware/regions.
- Key services: Auto Scaling, Graviton (ARM) instances, serverless, right-sizing.

---

## How to use the pillars on the exam

Map question keywords to pillars, then to services:

| Keyword in question | Pillar | Likely answer direction |
|---------------------|--------|-------------------------|
| "no single point of failure", "survive AZ loss" | Reliability | Multi-AZ, ELB, ASG |
| "least privilege", "encrypt", "audit" | Security | IAM roles, KMS, CloudTrail |
| "lowest cost", "pay only for use" | Cost Optimization | Spot, serverless, lifecycle |
| "lowest latency", "fastest" | Performance Efficiency | CloudFront, DAX, caching |
| "automate deployments", "monitor" | Operational Excellence | CloudFormation, CloudWatch |

## The 5 design principles that show up most
1. **Scale horizontally** (many small) instead of vertically (one big).
2. **Automate** everything (IaC, Auto Scaling, self-healing).
3. **Decouple** components (SQS/SNS/EventBridge).
4. **Design for failure** — assume everything fails; build redundancy.
5. **Stop guessing capacity** — use elastic, on-demand resources.
