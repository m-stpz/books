# Distributed Data

Part 1:

- aspects of data systems when data is stored on a single machine

Part 2:

- what happens if multiple machines are involved in storage/retrieval of data

## Why distribute data?

1. Scalability: spreading load
2. Fault tolerance/high availability: if one machine goes down, you have a backup
3. Latency: data is located closer to users

## Scaling to Higher Load

### Scaling up/Vertical scaling

A single machine, or a shared-memory architecture

Pros:

- Simpler
  - to debug
  - to architect
  - less variables to take into account

Cons:

- Single point of failure
- One geographical location
- There's a limit of how much you can increase computationally a machine

### Shared-Nothing Architectures/Horizontal scaling

Multiple nodes. Each node with its CPU, RAM, and disks

- Coordination is done through software

Pros:

- Redundancy
- Low-latency
- No single point of failure
- Scalable

Cons:

- More complex
  - it becomes harder to move data around in a consistent and predictable way

## Replication vs Partitioning

Two ways data is distributed accross multiple nodes

1. Replication: copies of the same data
   - Same data across multiple nodes (possibly in different locations)
   - Redundancy
2. Partitioning / Sharding: slices of the data spread around
   - Db is divided into smaller subsets (partitions)
