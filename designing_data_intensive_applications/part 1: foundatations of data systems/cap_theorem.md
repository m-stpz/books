# CAP Theorem

- Consistency, Availability and Partition Tolerance
  - We have have only 2 of these 3
  - Partition tolerance is a must. We must be able to deal with network failures. So the question is:
    - consistency or availability?

## When to choose consistency

- Systems that need:
  - strong consistency read after write
  - every read must return the last write
  - the data can't be stale

- Examples:
  - banks
  - ticket booking
  - ordering system
  - warehouse system

## When to choose availability

- If it's fine that some of the data isn't the most up to date, we should choose availability

- Examples:
  - most software would live here
