# Exam-Day Strategy & Question Technique

## The format (SAA-C03)
- 65 questions (50 scored + 15 unscored), 130 minutes → ~2 min per question.
- Multiple choice (1 of 4) and multiple response (2+ of 5+).
- Passing score 720/1000. No penalty for wrong answers — **never leave a blank**.

## Time management
- First pass: answer what you know fast. Flag anything that takes >2 min and move on.
- Second pass: return to flagged questions with remaining time.
- Watch the clock: ~25 questions done by the 50-min mark keeps you on pace.

## The 4-step question technique
1. **Read the actual question line first** (the last sentence). It tells you what's being optimized: cost? latency? availability? security?
2. **Identify the keywords/constraints**: "most cost-effective", "least operational overhead", "highly available", "minimal latency", "no code changes".
3. **Eliminate wrong answers.** Usually 2 are clearly wrong; you choose between the last 2.
4. **Pick the option that best matches the optimized dimension**, not just a technically-working one.

## Keyword → intent decoder
| Phrase | They want |
|--------|-----------|
| "most cost-effective" / "minimize cost" | cheapest option that still works |
| "least operational overhead" / "least management" | managed/serverless (Lambda, Fargate, Aurora Serverless, S3) |
| "highly available" / "fault tolerant" | Multi-AZ, ELB, ASG, replication |
| "decouple" / "absorb spikes" / "no lost messages" | SQS |
| "real-time" | Kinesis Data Streams |
| "lowest latency" | CloudFront / caching / Global Accelerator |
| "no code changes" | DAX for DynamoDB, RDS Multi-AZ failover |
| "private connectivity, no internet" | VPC endpoints / PrivateLink / Direct Connect |

## Elimination heuristics
- "Least operational overhead" → prefer managed/serverless over self-managed EC2.
- If two options both work, the cheaper or more managed one usually wins (match the keyword).
- Storing long-term credentials on instances is almost always wrong → IAM roles.
- Root account usage is almost always wrong.
- Answers that require custom code when a managed feature exists are usually distractors.
- "Multi-AZ" for availability, "Read Replica" for read scaling — don't confuse.

## Mindset
- Don't overthink: pick the AWS-recommended, Well-Architected answer.
- Flag and move on; a hard question is worth the same as an easy one.
- Trust elimination — removing 2 wrong answers doubles your odds.

## Before you start
- Read the question stem and the final ask carefully; distractors exploit skimming.
- There's no penalty for guessing — answer every question.
