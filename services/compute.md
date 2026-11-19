# Compute Services (SAA-C03)

## EC2 (Elastic Compute Cloud)
Virtual servers. You manage the OS and runtime.
- **Instance families**: General (M, T), Compute (C), Memory (R, X), Storage (I, D), Accelerated/GPU (P, G).
- **Graviton (ARM)** instances = better price/performance + sustainability.
- **Purchasing**: On-Demand, Reserved, Savings Plans, Spot, Dedicated Hosts/Instances.
- **AMI** — image used to launch instances. **User data** — bootstrap scripts at launch.
- **Instance store** (ephemeral) vs **EBS** (persistent).

## Auto Scaling Group (ASG)
- Maintains desired capacity; replaces unhealthy instances; spans multiple AZs.
- Policies: target tracking (e.g., keep CPU at 50%), step scaling, scheduled, predictive.
- Launch template defines what to launch. Works with ELB health checks.

## Elastic Load Balancing (ELB)
| Type | Layer | Use |
|------|-------|-----|
| ALB | 7 (HTTP/S) | Path/host routing, microservices, containers |
| NLB | 4 (TCP/UDP) | Ultra-high performance, static IP, low latency |
| GWLB | 3/4 | Deploy virtual appliances (firewalls) |

## Lambda (serverless functions)
- Event-driven, auto-scales per request, pay per invocation + duration.
- Max 15-min timeout; memory 128MB–10GB (CPU scales with memory).
- Triggers: API Gateway, S3, DynamoDB Streams, SQS, SNS, EventBridge.
- Good for spiky/unpredictable workloads; no idle cost.

## Containers
- **ECS** — AWS-native orchestration (EC2 launch type or Fargate).
- **EKS** — managed Kubernetes.
- **Fargate** — serverless containers; no node management; pay per task.
- **ECR** — container image registry.

## When to pick what
| Need | Pick |
|------|------|
| Full OS control / legacy apps | EC2 |
| Event-driven, spiky, no servers | Lambda |
| Containerized microservices | ECS/EKS |
| Containers without managing nodes | Fargate |
| Deepest discount for interruptible work | Spot EC2 |
