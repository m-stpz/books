# Chapter 1: reliable, scalable, and maintainable applications

- Many applications today are data-intensive, instead of compute-intensive
- Data-intensive application is built from standard building blocks that provide commonly needed functionality

Many applications need to:

- Store data so they, or another application, can find it again later (databases)
- Remember the result of an expensive operation, to speed up reads (cache)
- Allow users to search data by keyword or filter it in various ways (search indexes)
- Send a message to another process, to be handled async (stream processing)
- Periodically crunch a large amount of accumulated data (batch processing)

## Thinking about data systems

- How do we ensure that the data remains correct or complete, even when things go wrong internally?
- How do you provide consistently good performance to clients, even when parts of the systems are degraded?
- How do you scale to handle increase in load?
- What does a good API for the service look like?

### 3 concerns that are important in software systems

Reliability

- The system should continue to work correctly (performing the correct function at the desired level of performance) even in the face of adversity (hardware or software faults, and even human error)

Scalability

- As the system grows (in data volume, traffic volume, or complexity), there should be reasonable ways of dealing with the growth

Maintainability

- Over time, many different people will work on the system (enginerring and operations, both maintaining current behavior and adapting the system to new use cases), and they should all be able to work on it productively

### Reliability

- Software performs the function the user expected
- It can tolerate the user making mistakes/using the software in unexpected ways
- Its performance is good enough for the required use case, under the expected load and data volume
- System prevents any unauthorized access and abuse

> Continuing to work correctly, even when things go wrong

- Things that can go wrong -> faults
- Systems that can anticipate and cope with them are called resilient/fault-tolerant
- It only makes sense to talk about tolerating certain types of faults
- It's best to design fault-tolerance mechanisms that prevent faults (component) from causing failure (system)

#### Software faults

- Sometimes it happens that bug lie dormant for a long time until they're trigger but some set of circumstances
- It's revealed that the software is making some kind of assumption about its enviromnent, and while being true most of the time, it stops being true for some reason

#### Human errors

- Design systems in a way that minimize the opportunity for error
  - well-designed abstractions and APIs
  - admin interface
- Meaning, make it easy to do the "right thing" and discourage "the wrong thing"
- Provide fully feature non-production sandbox environments where people can explore and experiment safely
  - using real data, without affecting real users
- Test throughly at all levels
- Allow quick recovery and roll-back
- Detailed and clear monitoring [telemetry]

### Scalability

- Just because a system is working well today, it doesn't mean it will continue to do so in the future
- Common degradation reason is increased load
- Scalability = term used to describe a system's ability to cope with increased load

#### Describing load

- First, we need to describe the current load on the system
  - load can be described with a few numbers = load parameters

Possible load parameters [the best choice depends on the architecture of your system]

- Request per second to a web serves
- Ratio of reads to writes in the db
- Number of simultaneously active users

> fan-out [term borrowed from electrical engineering]: the N of requests to other services needed to make to serve the request

##### Example: Twitter

Main operations:

1. post tweet
   - user publishes a message to their followers (4,6k requests/second | 12k req/sec peak)
   - almost 2 order of magnitude lower than the home timeline (factor of 10)
     - something increase/decrease 10x (10^1)
     - 1
     - 1 order of magnitude = 10
     - 2 orders of magnitude = 100/\*\*/////sdfoisjahfdisudhfiusdhfiusdhfiusdhfiusdhfiu
     - 3 orders of magnitude = 1000
2. home timeline
   - user view tweets posted by people they follow (300k req/sec)

#### Describing performance

In an ideal world, the running time of a batch job is the size of the dataset divided by the throughput

> running_time_job = dataset_size / throughput

Throughput = number of records we can process per second

- In online systems, what's usually more important is the service's response time
  - time between client sending a request and getting a response

##### Latency and response time

- Latency and response time are often used interchangeable, however, they're different
- Response time = what client sees
  - plus time to process the request [service time]
  - plus network and queuing delays
- Latency = duration that a request is waiting to be handled
  - during which is latent, awaiting service

##### Response time

- We should think about Response time not as a single value, but a distribution of values over time that you can measure

- What might cause slower requests?
  - random additional latency
  - loss of a network packet and TCP retransmission
  - garbage collection pause
  - page fault forcing a read from disk
  - mechanical vibrations on the server rack
  - ...

- To measure your response time, it's better to use percentiles
  - list your response time
  - sort them from fastest to slowest
  - median is the halfway point
    - For example, if your median response time is 200ms, that means half your requests return in less than 200ms and half in more than that
    - median = 50th percentile (p50)

- How bad are my outliers?
  - look at the higher percentiles (the slowest responses)
    - 95th, 99th, 99.9th (p95, p99, p999)
    - meaning that 95% of requests are faster than that particular threshold
  - High percentiles of response times (tail latencies) are important. They directly influence the user's experience of the service
  - Amazon describe response time requirements for internal services in terms of the 99.9th percentile, even though it only affects 1 in 1000 requests
    - Why?
      - Because the customers with the slowest requests are often those who have the most data on their accounts
        - because they have done many purchases (meaning, the most valuable customers)

- SLOs: Service level objectives
- SLAs: Service level agreements
