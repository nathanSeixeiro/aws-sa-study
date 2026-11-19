# Domain 1: Design Secure Architectures (30%)

The heaviest domain. If you master one area, make it this one.

## Task statements
1. Design secure access to AWS resources
2. Design secure workloads and applications
3. Determine appropriate data security controls

---

## 1. Identity & Access Management (IAM)

**Core building blocks**
- **Users** — long-lived identities for humans/apps (avoid for apps; prefer roles).
- **Groups** — attach policies to a group, add users to it. Easier management.
- **Roles** — temporary credentials, assumed by services, users, or federated identities. The preferred mechanism for EC2, Lambda, cross-account, and federation.
- **Policies** — JSON documents granting/denying permissions. Identity-based (attached to user/group/role) vs resource-based (attached to S3 bucket, SQS queue, etc.).

**Golden rules for the exam**
- **Least privilege** — grant only what's needed.
- **Never use the root account** for daily work; enable MFA on it and lock it away.
- **Use IAM roles for EC2/Lambda** instead of embedding access keys.
- **IAM is global** (not Region-scoped).
- Policy evaluation: explicit **Deny** always wins over any Allow.

**Policy types to recognize**
- Identity-based, resource-based, permissions boundaries, Service Control Policies (SCPs in Organizations), session policies.

## 2. Federation & multi-account

- **IAM Identity Center** (successor to AWS SSO) — central workforce access across accounts.
- **Amazon Cognito** — app user sign-up/sign-in. *User pools* = authentication (who you are). *Identity pools* = authorization to AWS resources (temporary credentials).
- **SAML 2.0 / OIDC** federation for corporate directories.
- **AWS Organizations + SCPs** — guardrails across many accounts. SCPs set the *maximum* permissions; they don't grant.
- **STS** (Security Token Service) — issues temporary credentials (AssumeRole).

## 3. Encryption

- **At rest** vs **in transit** (TLS).
- **KMS** — managed keys. AWS managed keys vs customer managed keys (CMK, more control + rotation + policy). Envelope encryption.
- **CloudHSM** — dedicated hardware security module when you need single-tenant key control / compliance.
- **S3 encryption options**: SSE-S3 (AWS keys), SSE-KMS (KMS keys, audit + rotation), SSE-C (customer-provided keys), client-side.
- **ACM** (Certificate Manager) — free public TLS certs for ELB, CloudFront, API Gateway.

## 4. Network security

- **Security Groups** — instance-level, **stateful** (return traffic auto-allowed), allow rules only.
- **Network ACLs** — subnet-level, **stateless** (must allow both inbound AND outbound), allow + deny rules.
- **VPC endpoints** — private connectivity to AWS services without internet (Gateway endpoints for S3/DynamoDB; Interface endpoints / PrivateLink for most others).
- **Edge**: AWS WAF (layer-7 filtering, SQLi/XSS rules), AWS Shield (DDoS; Standard free, Advanced paid), CloudFront + Shield for edge protection.

## 5. Secrets, auditing, detection

- **Secrets Manager** — stores secrets with automatic rotation (RDS integration). 
- **SSM Parameter Store** — config + secrets (SecureString); cheaper, no built-in rotation.
- **CloudTrail** — records API calls (the "who did what" audit log).
- **AWS Config** — tracks resource configuration + compliance over time.
- **GuardDuty** — intelligent threat detection from logs.
- **Amazon Inspector** — automated vulnerability scanning of EC2/ECR/Lambda.
- **Macie** — discovers and protects sensitive data (PII) in S3.

---

## Decision cues (keyword → answer)
| If the question says... | Think... |
|-------------------------|----------|
| "no long-term credentials on the instance" | IAM role for EC2 |
| "temporary access for federated users" | STS / IAM Identity Center / Cognito |
| "audit trail of key usage / rotate keys" | SSE-KMS with customer managed key |
| "block traffic at the subnet level" | NACL |
| "private access to S3 without internet" | VPC Gateway endpoint |
| "automatically rotate database password" | Secrets Manager |
| "who made this API call?" | CloudTrail |
| "detect PII in S3" | Macie |

## Common exam traps
- Security Group = stateful; NACL = stateless. This distinction is tested constantly.
- SCPs don't grant permissions, they cap them.
- Explicit Deny overrides any Allow.
- Root account should only set up the account + billing, then be locked with MFA.

## My notes
<!-- fill in as you study -->
