# Security, Identity & Governance Services (SAA-C03)

## Identity
- **IAM** — users, groups, roles, policies. Least privilege. Roles for services. Global.
- **STS** — temporary credentials (AssumeRole, federation).
- **IAM Identity Center** — central workforce SSO across accounts.
- **Cognito** — app auth. User pools (authentication) vs identity pools (AWS access).
- **AWS Organizations + SCPs** — multi-account guardrails (SCPs cap, don't grant).

## Encryption & secrets
- **KMS** — managed keys, envelope encryption, rotation, audit via CloudTrail.
- **CloudHSM** — dedicated HSM, single-tenant, compliance.
- **ACM** — free public TLS certs for ELB/CloudFront/API Gateway.
- **Secrets Manager** — secrets with automatic rotation (RDS integration).
- **SSM Parameter Store** — config + SecureString secrets; cheaper; manual rotation.

## Network protection
- **Security Groups** (stateful, instance) / **NACLs** (stateless, subnet).
- **WAF** — layer-7 web filtering (SQLi, XSS, rate limiting).
- **Shield** — DDoS protection (Standard free; Advanced paid + support).
- **Firewall Manager** — centrally manage WAF/Shield/SG across accounts.
- **Network Firewall** — managed stateful network firewall for VPCs.

## Detection, audit & compliance
- **CloudTrail** — API call audit log ("who did what, when").
- **AWS Config** — resource configuration history + compliance rules.
- **GuardDuty** — ML threat detection from logs.
- **Inspector** — vulnerability scanning (EC2, ECR, Lambda).
- **Macie** — discover/protect sensitive data (PII) in S3.
- **Security Hub** — aggregates security findings.
- **Trusted Advisor** — best-practice checks (cost, security, fault tolerance, limits).

## Decision cues
| Need | Pick |
|------|------|
| Temporary creds for EC2/Lambda | IAM role + STS |
| Rotate DB password automatically | Secrets Manager |
| Audit of all API activity | CloudTrail |
| Check resources against compliance rules | AWS Config |
| Detect threats from account activity | GuardDuty |
| Find PII in S3 | Macie |
| Block SQL injection on a web app | WAF |
| Protect against DDoS at scale | Shield Advanced |
