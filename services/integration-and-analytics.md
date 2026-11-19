# Application Integration & Analytics (SAA-C03)

## Messaging & integration
- **SQS** — durable queue; decouple producer/consumer; absorb spikes. Standard (at-least-once) vs FIFO (exactly-once, ordered). Visibility timeout, DLQ for poison messages.
- **SNS** — pub/sub fan-out; push to SQS, Lambda, HTTP, email, SMS. FIFO topics available.
- **EventBridge** — event bus; routes events from AWS services + SaaS with rich filtering; scheduled rules (cron).
- **Step Functions** — serverless workflow orchestration with state, retries, branching.
- **API Gateway** — managed REST/HTTP/WebSocket APIs; throttling, caching, auth integration.
- **AppSync** — managed GraphQL.
- **Amazon MQ** — managed ActiveMQ/RabbitMQ (for migrating existing apps using standard protocols).

## Streaming & ingestion
- **Kinesis Data Streams** — real-time streaming (shards, custom consumers).
- **Kinesis Data Firehose** — load streams into S3/Redshift/OpenSearch (near real-time, no code).
- **Amazon MSK** — managed Apache Kafka.

## Analytics
- **Athena** — serverless SQL directly on S3 (pay per query scanned).
- **Glue** — serverless ETL + Data Catalog.
- **EMR** — managed Hadoop/Spark big data.
- **Redshift** — data warehouse (see databases.md).
- **OpenSearch** — search + log analytics.
- **QuickSight** — BI dashboards.
- **Lake Formation** — build/secure data lakes on S3.

## Decision cues
| Need | Pick |
|------|------|
| Decouple + buffer work, one consumer each | SQS |
| Fan-out one message to many subscribers | SNS |
| Route events by rules / scheduled jobs | EventBridge |
| Coordinate a multi-step workflow | Step Functions |
| Real-time streaming ingestion | Kinesis Data Streams |
| Land streaming data in S3 with no code | Kinesis Data Firehose |
| Ad-hoc SQL on S3 data, serverless | Athena |
| Managed ETL / data catalog | Glue |
| Migrate existing RabbitMQ/ActiveMQ app | Amazon MQ |

## Traps
- SQS = queue (pull, one consumer per message). SNS = pub/sub (push, many subscribers).
- Firehose = near-real-time delivery to storage; Data Streams = real-time custom processing.
- Amazon MQ only when you must keep standard messaging protocols (JMS/AMQP); otherwise prefer SQS/SNS.
