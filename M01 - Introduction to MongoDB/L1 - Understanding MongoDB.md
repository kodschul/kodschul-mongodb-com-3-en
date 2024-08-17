
## What is MongoDB?

MongoDB is a document-oriented NoSQL database known for its high performance, scalability and flexibility. Unlike traditional relational databases, MongoDB uses a flexible, JSON-like schema for storing data, making it ideal for applications with rapidly changing or unstructured data.

### Definition and basic concepts

#### 1. Document-oriented model

MongoDB stores data in the form of documents organized in collections. A document is a JSON-like structure that contains fields and value pairs.

- **Example of a document**:
  ```json
  {
    “_id": ‘12345’,
    “name": ‘John Doe’,
    “email": ‘john.doe@example.com’,
    “age": 29
  }
  ```

#### 2. Schema flexibility
Unlike relational databases, MongoDB does not require a fixed schema. Documents in a collection do not have to have the same schema, which enables flexible and dynamic development.

Advantage: Developers can change data structures as required without having to change the entire database structure.

#### 3. Collections and documents
Collections: Equivalent to tables in relational databases, but without a fixed schema.
Documents: Equivalent to rows in relational databases, but with flexible, JSON-like structures.

#### 4. Query language
MongoDB uses a powerful, flexible query language based on JSON that supports a variety of query and aggregation operations.

- Example of a query:
```json
  db.users.find({ “age”: { “$gt”: 25 } })
  ```

### Advantages of MongoDB compared to relational databases
1. flexible schema
Advantage: MongoDB allows data to be stored without having to define a schema beforehand. This is particularly useful for applications where the data structure is frequently changed or extended.
2. horizontal scalability
Advantage: MongoDB supports sharding, a method of horizontal scaling in which data is distributed across multiple servers (shards). This makes it possible to efficiently manage large amounts of data and optimize performance.
3. high performance
Advantage: MongoDB is optimized for high read and write speeds. It uses a memory-based approach to data processing that improves performance for data-intensive applications.
4. easy replication and high availability
Advantage: MongoDB offers built-in replication mechanisms that copy the data to multiple servers. This ensures high availability and data redundancy in the event of a server failure.
5. rich query language
Benefit: MongoDB's query language is flexible and powerful, supporting complex queries, aggregations and text-based searches, giving developers more freedom and functionality.
6. geospatial support
Benefit: MongoDB provides built-in support for geospatial data and queries, making it ideal for applications that use location data.
7. JSON-like format (BSON)
Benefit: MongoDB stores data in BSON (Binary JSON) format, which enables efficient document storage and retrieval. BSON also supports additional data types that are not available in JSON, such as date and binary data.

