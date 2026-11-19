# SAA-C03 Study Plan

A flexible plan. Compress or stretch the weeks to fit your schedule. The habit that matters
most: read a little every day + do practice questions every few days.

## 6-week plan (adjust as needed)

### Week 1 — Foundations + Security (Domain 1, 30%)
- Read `domains/01-secure-architectures.md` + `services/security.md`.
- Core concepts: IAM roles vs users, policies, encryption (KMS), SG vs NACL, VPC endpoints.
- Do `practice/practice-set-01.md`.

### Week 2 — Networking + Compute
- Read `services/networking.md` + `services/compute.md`.
- VPC layout, NAT vs IGW, ELB types, Auto Scaling, EC2 purchasing options, Lambda.
- Do `practice/practice-set-02.md`.

### Week 3 — Resilient Architectures (Domain 2, 26%)
- Read `domains/02-resilient-architectures.md` + `services/integration-and-analytics.md`.
- Multi-AZ, SQS/SNS decoupling, RDS Multi-AZ vs Read Replicas, DR strategies.

### Week 4 — High-Performing Architectures (Domain 3, 24%)
- Read `domains/03-high-performing-architectures.md` + `services/databases.md` + `services/storage.md`.
- Caching (DAX/ElastiCache/CloudFront), DynamoDB, EBS/EFS/FSx, storage classes.
- Do `practice/practice-set-03.md`.

### Week 5 — Cost Optimization (Domain 4, 20%) + Well-Architected
- Read `domains/04-cost-optimized-architectures.md` + `best-practices/well-architected-framework.md`.
- Spot/RI/Savings Plans, S3 lifecycle + Intelligent-Tiering, data transfer costs.
- Review `best-practices/architecture-patterns.md`.

### Week 6 — Review + mock exams
- Re-read all four domain files + the cheatsheet.
- Re-test everything in `notes/weak-spots.md`.
- Run full timed mock exams; aim for 80%+ consistently before booking.

## Daily micro-routine (30–45 min)
1. Read one section of a domain/service file (10 min).
2. Add anything new to your notes (5 min).
3. Do 5 practice questions (15 min).
4. Log results + move misses to `notes/weak-spots.md` (5 min).

## Recommended official resources
- SAA-C03 Exam Guide (authoritative scope):
  https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03.html
- AWS Skill Builder (official training + practice): https://skillbuilder.aws
- AWS Well-Architected Framework: https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html
- AWS service FAQs (great exam prep per service).

## Readiness checklist (book when all true)
- [ ] Scoring 80%+ on mixed practice sets, timed.
- [ ] Can explain each core service in one sentence + when to pick it.
- [ ] Comfortable with all decision cues in the domain files.
- [ ] Weak-spots list is empty or re-tested green.
