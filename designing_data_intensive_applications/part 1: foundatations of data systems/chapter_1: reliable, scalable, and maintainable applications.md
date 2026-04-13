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
