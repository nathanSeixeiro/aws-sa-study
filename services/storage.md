# Storage Services (SAA-C03)

## S3 (object storage)
- Buckets + objects; 11 nines durability; virtually unlimited.
- **Storage classes**: Standard, Standard-IA, One Zone-IA, Intelligent-Tiering, Glacier Instant Retrieval, Glacier Flexible Retrieval, Glacier Deep Archive.
- **Lifecycle rules** — auto-transition/expire objects.
- **Versioning** — keep multiple versions; protects against overwrite/delete.
- **Replication** — CRR (cross-Region) / SRR (same-Region); requires versioning.
- **Encryption** — SSE-S3, SSE-KMS, SSE-C, client-side.
- **Access control** — bucket policies, IAM, ACLs (legacy), Block Public Access, presigned URLs, Access Points.
- **Object Lock** — WORM/compliance, prevent delete/overwrite.
- **Performance** — 3,500 PUT / 5,500 GET per prefix/sec; multipart upload; Transfer Acceleration.

## EBS (block storage for EC2)
- Attached to a single instance (same AZ); persistent.
- Types: gp3 (default SSD, independent IOPS/throughput), io1/io2 (high IOPS), st1 (throughput HDD), sc1 (cold HDD).
- Snapshots → S3; copy across Regions; encryption with KMS.
- **Multi-Attach** (io1/io2) for a few instances.

## EFS (shared file storage)
- Managed NFS; many Linux instances concurrently; auto-scales.
- Standard vs One Zone; IA storage class + lifecycle for cost.

## FSx
- **FSx for Windows File Server** — SMB shares for Windows.
- **FSx for Lustre** — HPC/ML, integrates with S3.
- Also FSx for NetApp ONTAP, OpenZFS.

## Instance Store
- Ephemeral, physically attached, very high IOPS, lost on stop/terminate.

## Storage Gateway (hybrid)
- File / Volume / Tape gateways bridging on-prem to AWS storage.

## Pick-the-right-storage
| Need | Pick |
|------|------|
| Object store for files/backups/web | S3 |
| Disk for a single EC2 instance | EBS |
| Shared files across many Linux boxes | EFS |
| Windows file shares | FSx for Windows |
| Cheapest long-term archive | Glacier Deep Archive |
| Unknown/changing access pattern | S3 Intelligent-Tiering |
