# Designing data-intensive applications

> The big ideas behind reliable, scalable, and maintainable systems

Table of contents

## Part 1. Foundations of data systems

### Chapter 1. Reliable, scalable, and maintainable applications

- Thinking about data systems
- Reliability
  - Hardware faults
  - Software errors
  - Human erros
  - How important is reliability?
- Scalability
  - Describing load
  - Describing performance
  - Approaches for coping with load
- Maintainability
  - Operability: making life easy for operations
  - Simplicity: managing complexity
  - Evolvability: making change easy

### Chapter 2. Data models and query languages

- Relational model versus document model
  - The birth of NoSQL
  - The object-relational mismatch
  - Many-to-one and many-to-many relationships
  - Are document databases repeating history?
  - Relational versus document databases today
- Query languages for data
  - Declarative queries on the web
  - MapReduce querying
- Graph-like data models
  - Property graphs
  - The cypher query language
  - Graph queries in SQL
  - Triple-stores and SPARQL
  - The foundation: datalog

### Chapter 3. Storage and retrieval

- Data structures that power your db
  - Hash indexes
  - SSTables and LSM-Trees
  - B-trees
  - Comparing B-trees and LSM-trees
  - Other indexing structures
- Transaction processing or analytics?
  - Data warehousing
  - Stars and snowflakes: schemas for analytics
- Column-oriented storage
  - Column compression
  - Sort order in column storage
  - Writing to column-oriented storage
  - Aggregation: data cubes and materialized views

### Chapter 4. Encoding and evolution

- Formats for encoding data
  - Language-specific formats
  - JSON, XML, and binary variants
  - Thrift and protocol buffers
  - Avro
  - The merits of schemas
- Modes of dataflow
  - Dataflow through databases
  - Dataflow through services: REST and RCP
  - Message-passing dataflow

## Part 2. Distributed data

### Chapter 5. Replication

- Leaders and followers
  - Sync vs async replication
  - Setting up new followers
  - Handling node outages
  - Implementation of replication logs
- Problems with replication lag
  - Reading your own writes
  - Monotonic reads
  - Consistent prefix reads
  - Solutions for replication lag
- Multi-leader replication
  - Use cases for multi-leader replication
  - Handling write conflicts
  - Multi-leader replication topologies
- Leaderless replication
  - Write to the db when a node is down
  - Limitations of quorum consistency
  - Sloppy quorums and hinted handoff
  - Detecting concurrent writes

### Chapter 6. Partitioning

- Partitioning and replication
- Partitioning of key-value data
  - Partitioning by key range
  - Partitioning by hash of key
  - Skewed workloads and relieving hot spots
- Partitioning and secondary indexes
  - Partitioning secondary indexes by document
  - Partitioning secondary indexes by term
- Rebalancing partitions
  - Strategies for rebalancing
  - Operations: automatic or manual rebalancing
- Request routing
  - Parallel query execution

### Chapter 7. Transactions

- The slippery concept of a transaction
  - The meaning of ACID
  - Single-object and multi-object operations
- Weak isolation levels
  - Read committed
  - Snapshot isolation and repeatable read
  - Preventing lost updates
  - Write skew and phantoms
- Serializability
  - Actual serial execution
  - Two-phase locking (2PL)
  - Serializable snapshot isolation (SSI)

### Chapter 8. The trouble with distributed systems

- Faults and partial failures
  - Cloud computing and supercomputing
- Unreliable networks
  - Network faults in practice
  - Detecting faults
  - Timeouts and unbounded delays
  - Sync versus async networks
- Unreliable clocks
  - Monotonic versus time-of-day clocks
  - Clock synchronization and accuracy
  - Relying on synced clocks
  - Process pauses
- Knowledge, truth, and lies
  - The truth is defined by the majority
  - Byzantine faults
  - System model and reality

### Chapter 9. Consistency vs. consensus

- Consistency guarantees
- Linearizability
  - What makes a system lineariazable?
  - Relying on Linearizability
  - Implemeting Linearizable systems
  - The cost of Linearizability
- Ordering guarantees
  - Ordering and causality
  - Sequence number ordering
  - Total order broadcast
- Distributed transactions and consensus
  - Atomic commit and two-phase commit (2PC)
  - Distributed transactions in practice
  - Fault-tolerant consensus
  - Membership and coordination services

## Part 3. Derived data

### Chapter 10. Batch processing

- Batch processing with unix tools
  - Simple logs analysis
  - The unix philosophy
- MapReduce and Distributed Filesystems
  - MapReduce Job Execution
  - Reduce-Side Joins and groupings
  - Map-side joins
  - The output of batch workflows
  - Comparing Hadoop to Distributed dbs
- Beyond MapReduce
  - Materialization of intermediate state
  - Graphs and iterative processing
  - High-level APIs and languages

### Chapter 11. Stream processing

- Transmitting event streams
  - Messaging systems
  - Partitioned logs
- Dbs and streams
  - Keeping systems in sync
  - Change data capture
  - Event sourcing
  - State, streams, and immutability
- Processing streams
  - Uses of stream processing
  - Reasoning about time
  - Stream joins
  - Fault tolerance

### Chapter 12. The future of data systems

- Data integration
  - Combining specialized tools by deriving data
  - Batch and stream processing
- Unbundling dbs
  - Composing data storage technologies
  - Designing applications around dataflow
  - Observing derived state
- Aiming for correctness
  - The end-to-end argument for dbs
  - Enforcing constraints
  - Timeliness and integrity
  - Trust, but verify
- Doing the right thing
  - Predictive analytics
  - Privacy and tracking
