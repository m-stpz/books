# Replication

- Replication: keeping a copy of the same data on multiple machines that are connected via a network
  - for a long time, except in research, many developers assumed that a database consisted of only one node
  - Replication in databases started being studied in 1970, and its principles haven't changed much
  - Mainstream usage of distributed databases is more recent

Why would you want to replicate data?

- Keep data geographically close to the users -> reduces latency
- Allow system to continue working even with some faulty parts | Avoid single point of failure -> increase availability
- Scale number of machines that can serve read queries -> increase throughput

All the difficulty in replication lies in how to handle changes in the replicated data.

- If the data in one portion of the system is updated, how will the other parts know?
- There are 3 common algorithms for replicating changes across the nodes
  - single-leader
  - multileader
  - leaderless

- Should we use sync or asyn replication?
- How do we handle failed replicas?

## Leaders and followers

- Replica: each node that stores a copy of the database
  - With replicas the question is: how do we ensure the data ends up in all replicas?

```
replica 1:
    - user: 123
        [write operations] -> needs to be propagated
    - name: "John" -> change to "John Doe"
    - profile_pic: "hey_mom.png" -> changed to "cat_photo.png"

replica 2:  -> eventually this replica will need to have the updated data
    - user: 123
    - name: "John"
    - profile_pic: "hey_mom.png"
```

- **Every write to the db needs to be processed by every replica**
