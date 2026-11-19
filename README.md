# AWS Certified Solutions Architect – Associate (SAA-C03) Study Repo

A complete, self-contained study repo for the SAA-C03 exam, built with Kiro Study Buddy.
Everything here is organized around the official exam domains and the AWS Well-Architected Framework.

## Exam at a glance

| Detail | Value |
|--------|-------|
| Exam | AWS Certified Solutions Architect - Associate (SAA-C03) |
| Questions | 50 scored + 15 unscored = 65 total |
| Time | 130 minutes |
| Passing score | 720 / 1000 |
| Level | Associate |

## Content domains

| # | Domain | Weight |
|---|--------|--------|
| 1 | Design Secure Architectures | 30% |
| 2 | Design Resilient Architectures | 26% |
| 3 | Design High-Performing Architectures | 24% |
| 4 | Design Cost-Optimized Architectures | 20% |

Heaviest domain: **Design Secure Architectures (30%)** — prioritize it.

## Repo layout

```
aws-sa/
├── README.md                         # this file — start here
├── study-plan.md                     # 6-week plan + daily routine + checklist
├── exam-strategy.md                  # question technique, keyword decoder, time mgmt
├── glossary.md                       # acronyms & terms
│
├── domains/                          # exam content by domain
│   ├── 01-secure-architectures.md       (30%)
│   ├── 02-resilient-architectures.md    (26%)
│   ├── 03-high-performing-architectures.md (24%)
│   └── 04-cost-optimized-architectures.md  (20%)
│
├── services/                         # service deep-dives
│   ├── service-cheatsheet.md            # one-glance "what + when"
│   ├── compute.md
│   ├── storage.md
│   ├── networking.md
│   ├── databases.md
│   ├── security.md
│   └── integration-and-analytics.md
│
├── best-practices/
│   ├── well-architected-framework.md    # the 6 pillars + how they map to questions
│   └── architecture-patterns.md         # 8 reference patterns
│
├── practice/
│   ├── practice-set-01.md               # 5 Qs (all domains)
│   ├── practice-set-02.md               # 7 Qs (networking, compute, security)
│   ├── practice-set-03.md               # 8 Qs (storage, db, performance, cost)
│   └── question-log.md                  # track attempts & accuracy
│
└── notes/
    └── weak-spots.md                    # topics to revisit before exam day
```

## How to study with Kiro

- Ask any question — Study Companion is always on
- `#scenario-practice` — Socratic guided scenarios
- `#service-comparator` — side-by-side service comparisons
- `#exam-simulator` — timed exam simulation with scoring
- `#question-breakdown` — four-step question deconstruction method

## Recommended path

1. Read `study-plan.md` and pick your pace.
2. Work domain by domain (`domains/`), pulling detail from `services/` as needed.
3. Internalize `best-practices/well-architected-framework.md` — the exam's backbone.
4. After each domain, do a practice set and log results in `practice/question-log.md`.
5. Move every miss into `notes/weak-spots.md` and re-test it.
6. Review `exam-strategy.md` before your final mock exams.
7. Book the exam when you consistently score 80%+ timed.

## Study totals in this repo
- 4 domain guides + 6 service deep-dives + cheatsheet
- Well-Architected Framework (6 pillars) + 8 architecture patterns
- Study plan, exam strategy, glossary
- 3 practice sets = 20 questions with full answer keys

> **Sourcing note:** Content is grounded in the official SAA-C03 exam guide and AWS service
> documentation. The Kiro Study Buddy power also bundles an AWS Documentation MCP server for
> live citations — it requires the `uv` package manager
> (https://docs.astral.sh/uv/getting-started/installation/) and can be reconnected from the
> MCP Server view once installed.
>
> Official exam guide:
> https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03.html
