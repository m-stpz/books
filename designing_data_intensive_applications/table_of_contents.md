# Designing data-intensive applications

> The big ideas behind reliable, scalable, and maintainable systems

Table of contents

## Part 1. Foundations of data systems

### Section 1. Reliable, scalable, and maintainable applications

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

### Section 2. Data models and query languages

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
  - The goundation: datalog

### Section 3. Storage and retrieval

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
