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

- As the system grows (in data volume, traffice volume, or complexity), there should be reasonable ways of dealing with the growth

Maintainability

- Over time, many different people will work on the system (enginerring and operations, both maintaining current behavior and adapting the system to new use cases), and they should all be able to work on it productively
