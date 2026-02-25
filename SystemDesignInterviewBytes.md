## Sharding and Replication 
- Sharding improves write throughput only if the partition key distributes write load evenly.
- In a sharded system, writes go to the primary node of the responsible shard. Reads go to that shard as well, but if replication is enabled, reads are typically offloaded to replicas to increase read throughput while preserving write capacity on the primary.
- Sharding increases write throughput by distributing write load across independent database nodes, while replication increases read throughput by adding more nodes that can serve read queries concurrently.
- Sharding increases write throughput by parallelizing write streams across independent storage engines, removing single-node CPU, WAL, and lock bottlenecks — provided the partition key evenly distributes write load.
- Replication increases read throughput by horizontally scaling read capacity via additional serving nodes, but does not improve write throughput and may reduce it under synchronous durability guarantees.
- In a sharded system, writes go to the primary node of the responsible shard. Reads go to that shard as well, but if replication is enabled, reads are typically offloaded to replicas to increase read throughput while preserving write capacity on the primary.

## Failure modes
### DB Failure modes
- If a shard primary crashes, writes become unavailable for that shard until failover. In async replication, there’s a data loss window equal to replication lag. So I’d evaluate durability requirements. For critical issue state changes, I’d use quorum writes to ensure at least two nodes persist the update before acknowledging success.
- Replica lag introduces stale reads. For read-after-write sensitive paths like issue updates, Implement session stickiness or lag-aware routing so immediate reads go to primary if lag exceeds threshold.
- Split brain is more dangerous than downtime. Ensure leader election requires majority quorum, and isolated nodes are fenced off to prevent dual-write divergence.
- Hot shards create partial degradation. Monitor per-shard QPS and rebalance heavy tenants using virtual shards, enabling traffic redistribution without full resharding.
- Classify database failures into leader failures, replication failures, partition failures, load imbalance failures, and data integrity failures.

- For leader failures, evaluate data loss window and quorum configuration.
- For replication failures, design lag-aware read routing.
- For partition scenarios, enforce majority-based leader election to prevent split brain.
- For load imbalance, monitor shard-level metrics and enable dynamic rebalancing.
- And for correctness failures, implement invariants validation and reconciliation jobs.
