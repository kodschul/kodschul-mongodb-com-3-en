
## MongoDB: Data model

MongoDB is a NoSQL database that works document-oriented. The MongoDB data model consists of documents that are organized in collections and databases. This model offers flexibility and scalability that are well suited to a wide range of applications. The structure and properties of document-based data models in MongoDB are described below.

### Documents

Documents are the basic unit of data in MongoDB and are stored in BSON (Binary JSON) format. Each document consists of a series of key-value pairs, similar to a JSON object. Documents can contain nested structures and have different schemas, even within the same collection.

#### Example document

```json
{
  “_id": ‘507f1f77bcf86cd799439011’,
  “name": ‘Alice’,
  “age": 29,
  “address": {
    “street": ‘123 Main St’,
    “city": ‘Metropolis’,
    “zip": ”12345”
  },
  “hobbies“: [”reading”, ‘hiking’, ‘coding’]
}
```

_id: A unique identifier for the document. MongoDB generates this value automatically if it is not specified.
name, age: Simple key-value pairs.
address: A nested document.
hobbies: An array of values.
### Collections
Collections are groupings of documents in MongoDB. A collection is similar to a table in relational databases, but without a fixed schema. All documents within a collection can have different structures, which offers great flexibility.

#### Properties of collections
Freedom from schemas: Documents within a collection can have different fields and data types.
Indexes: Collections can contain indexes on arbitrary fields to improve query performance.
Aggregation: MongoDB provides powerful aggregation frameworks to perform complex data analysis.
### Databases
Databases are containers for collections. A MongoDB instance can contain multiple databases that are isolated from each other. Each database has its own collections and documents.

#### Example of the database structure
Database: myDatabase
##### Collection: users
Documents: Several documents with user data
##### Collection: orders
Documents: Multiple documents with order data
### Structure and properties of document-based data models
#### Flexibility
Schema freedom: Documents in a collection do not have to have the same schema. This enables flexible and dynamic data modeling.
Nesting: Documents can contain nested documents and arrays, which enables complex data structures.
#### Efficiency
Embedding: Data that is frequently queried together can be embedded in a single document. This reduces the number of joins and increases query speed.
Indexes: MongoDB supports indexes on document fields, including nested fields and arrays, to optimize performance.
#### Scalability
Horizontal scaling: MongoDB supports sharding, a method of distributing data across multiple machines to keep pace with growing data volumes and query requirements.
Replication: MongoDB offers automatic replication and failover to ensure high availability and data security.

