# Common Architecture Patterns (SAA-C03)

These reference patterns answer a large share of exam questions. Learn to recognize them.

## 1. Classic 3-tier web app
- **Web/presentation tier**: CloudFront → ALB → EC2/ASG across multiple AZs.
- **App tier**: EC2/ASG or Lambda, stateless; session state in DynamoDB/ElastiCache.
- **Data tier**: RDS Multi-AZ (or Aurora), or DynamoDB.
- Static assets served from S3 + CloudFront.

## 2. Decoupled / event-driven
- Producer → **SQS** → worker fleet (ASG scales on queue depth).
- **SNS fan-out** → multiple SQS queues / Lambda.
- **EventBridge** routes events between services.
- Benefit: spikes absorbed, components fail independently.

## 3. Serverless web/API
- CloudFront → API Gateway → Lambda → DynamoDB.
- S3 static website hosting for the frontend.
- Cognito for auth.
- Pay-per-use, scales automatically, no servers to manage.

## 4. Highly available database
- **RDS Multi-AZ** for automatic failover.
- **Read Replicas** to offload read traffic.
- **ElastiCache** in front for hot reads.
- Aurora for higher performance + up to 15 replicas + Global Database for DR.

## 5. Static website / content delivery
- S3 (static hosting) + CloudFront (CDN) + Route 53 (DNS) + ACM (free TLS).
- Cheap, scalable, globally fast, no servers.

## 6. Hybrid connectivity
- **VPN** over the internet (quick, cheaper, variable performance).
- **Direct Connect** dedicated link (consistent, higher performance, longer lead time).
- **Transit Gateway** to connect many VPCs/accounts/on-prem at scale.
- **Storage Gateway** to bridge on-prem to S3/EBS.

## 7. Disaster recovery spectrum
Backup & Restore → Pilot Light → Warm Standby → Multi-Site Active/Active
(cheaper/slower ──────────────────────────────► pricier/faster)

## 8. Secure VPC layout
- Public subnets: ALB, NAT Gateway, bastion.
- Private subnets: app servers, databases (no direct internet).
- NAT Gateway for outbound internet from private subnets.
- VPC endpoints for private S3/DynamoDB access.
- Security Groups (instance) + NACLs (subnet).

## Pattern → requirement quick map
| Requirement | Pattern |
|-------------|---------|
| Survive AZ failure | Multi-AZ + ELB + ASG |
| Absorb traffic spikes without data loss | SQS queue |
| Global low-latency static content | S3 + CloudFront |
| No servers to manage | API Gateway + Lambda + DynamoDB |
| Private DB with controlled egress | Private subnets + NAT + endpoints |
| Cheapest DR | Backup & Restore |
