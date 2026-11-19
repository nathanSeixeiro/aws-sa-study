# Networking Services (SAA-C03)

## VPC (Virtual Private Cloud)
- Your isolated network. CIDR block, subnets (public/private), route tables.
- **Internet Gateway (IGW)** — internet access for public subnets.
- **NAT Gateway** — outbound internet for private subnets (managed, AZ-scoped, charged per hour + GB). NAT Instance is the legacy DIY option.
- **Security Groups** — instance-level, stateful, allow-only.
- **NACLs** — subnet-level, stateless, allow + deny.
- **VPC Peering** — connect two VPCs (no transitive routing).
- **Transit Gateway** — hub connecting many VPCs/accounts/on-prem at scale.
- **VPC Endpoints** — private access to AWS services. Gateway (S3, DynamoDB, free) vs Interface/PrivateLink (ENI, most services).
- **VPC Flow Logs** — capture network traffic metadata.

## Route 53 (DNS)
- Routing policies: simple, weighted, latency, failover, geolocation, geoproximity, multivalue.
- Health checks enable DNS failover.
- Alias records point to AWS resources (ALB, CloudFront, S3) for free.

## CloudFront (CDN)
- Caches content at edge locations; lowers latency.
- Origins: S3, ALB, custom HTTP. Integrates with WAF, Shield, ACM.
- OAC/OAI to restrict S3 access to CloudFront only.

## Global Accelerator
- Static anycast IPs + AWS backbone routing; for global TCP/UDP (non-HTTP) apps.
- Contrast with CloudFront (HTTP content caching).

## Hybrid connectivity
- **Site-to-Site VPN** — encrypted tunnel over internet; quick, variable performance.
- **Direct Connect (DX)** — dedicated private link; consistent, higher performance, longer provisioning.
- **Direct Connect + VPN** for encrypted private connectivity.

## Decision cues
| Need | Pick |
|------|------|
| Outbound internet from private subnet | NAT Gateway |
| Private S3 access, cut NAT cost | S3 Gateway endpoint (free) |
| Connect many VPCs at scale | Transit Gateway |
| DNS failover between Regions | Route 53 failover routing + health checks |
| Cache HTTP content globally | CloudFront |
| Static IP + backbone for TCP/UDP app | Global Accelerator |
| Consistent private link to on-prem | Direct Connect |
