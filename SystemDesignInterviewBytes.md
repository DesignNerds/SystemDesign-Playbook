## Sharding and Replication 
- Sharding improves write throughput only if the partition key distributes write load evenly.
- In a sharded system, writes go to the primary node of the responsible shard. Reads go to that shard as well, but if replication is enabled, reads are typically offloaded to replicas to increase read throughput while preserving write capacity on the primary.
- Sharding increases write throughput by distributing write load across independent database nodes, while replication increases read throughput by adding more nodes that can serve read queries concurrently.
- 
