# Principles of NoSQL Data Modeling

[MongoDB Universtiy](https://learn.mongodb.com/)
[YouTube MongoDB Lecture](https://www.youtube.com/watch?v=0XVmuyPGy-o)

**Core Principle: Data that is used together in the application is stored together in the database.**

Data Modeling: The process of defining how data is stored and the relationships that exist among different entities in your data.
Schema: The organization of data within a database.
Polymorphism: Each document in the database can be different.

Relationship Types
- One-to-One
- One-to-Many
- Many-to-Many

### Reference
Referencing: We refer to documents in another collection in our document.

References save the _id field of one document in another document as a link between the two

Benefits: 
- No duplication of data
- Smaller documents

Warning:
- Querying from multiple documents costs extra resources and impacts read performance

When to Reference:
- when the "many" side is a huge number
- for integrity on write operations on many-to-many
- when a piece is frequently used, but not the other and memory is an issue

### Embed
Embedding: We take related data and insert it into our document.

Embedding is typical for One-to-Many and Many-to-Many.

When to Embed:
- for integrity of read operations
- for integrity of write operations on one-to-one and one-to-many
- for data that is deleted or archived together
- by default

Benefits:
- Avoids application joins
- Provides better performance for read operations.
- Allows developers to update related data in a single write operation.

Warning:
- Embedding can make document very large over time.
- large documents have to read into memory in full, which can result in a slow application performance for your end user.
- Continuously adding data without limit creates unbounded documents.
- Unbounded documents may exceed the BSON document threshold of 16MB

### Avoid
- More than the document size of 16 MB
- Poor query performance
- Poor write performance
- Too much memory being used


## NoSQL Design Patterns
[Article](https://www.mongodb.com/blog/post/building-with-patterns-a-summary)
Approximation
Attribute
Bucket
Computed
Document Versioning
Extended Reference
Outlier
Preallocated
Polymorphic
Schema Versioning
Subset
Tree and Graph