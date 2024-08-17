
## MongoDB: Terms, wording and deployment models

MongoDB is a widely used NoSQL database that offers a flexible and scalable solution for storing and managing data. This guide provides an introduction to important terms and concepts as well as the different deployment models of MongoDB.

### Important terms and their meanings

- **Document**: The basic unit of data in MongoDB, similar to a row in a relational database. A document is a JSON-like structure consisting of field-value pairs.

-  Collection: A group of documents, similar to a table in a relational database. A collection exists within a database.

-  Database: A physical container structure for collections. Each database has its own files on the file system.

- **_id**: A unique identification field that is automatically assigned to each document. It serves as a primary key.

-  Query**: A command used to read documents from a collection. Queries can contain filters, projections and sorting.

- **Index**: A special data structure that increases the efficiency of queries. Indexes speed up the search by allowing a quick path to the desired data.

- **Shard**: A horizontal partitioning of the database where data is distributed across multiple machines to increase scalability.

- **Replica Set**: A group of MongoDB instances that contain the same data and provide high availability through automatic failover and redundancy.

### Different deployment models

MongoDB offers different deployment models that can be selected depending on scalability, availability and performance requirements.

#### 1. Single instance

A single MongoDB instance is the simplest form of deployment. It is well suited for development and test environments, but is not suitable for production environments due to the lack of failover and redundancy.

-  Features**:
  - Easy to install and manage.
  - No redundancy or automatic failover features.
  - Limited scalability.

-  Use case**: Development environments, prototyping, small applications.

#### 2. Replica Set

A replica set consists of multiple MongoDB instances (primary and secondary) that replicate data to ensure high availability and data redundancy.

- **Properties**:
  - A primary instance that accepts write operations.
  - One or more secondary instances that replicate the data of the primary instance and support read operations.
  - Automatic failover: If the primary instance fails, a secondary instance is automatically promoted to the new primary instance.

-  Use case**: Production environments where high availability and reliability are required.

#### 3. Sharded cluster

A sharded cluster distributes the data across multiple shards to enable horizontal scalability and high performance. Each shard is a separate replica set.

-  Features**:
  - Data is distributed across multiple shards based on a sharding key.
  - Supports the management of large amounts of data and high throughput requirements.
  - Each shard consists of a replica set that ensures availability and redundancy.

- **Components**:
  - **Shards**: Contain the actual data.
  - **Config Server**: Manage the metadata and configuration of the cluster.
  - **Query Router (mongos)**: Forward the queries to the corresponding shards.

-  Use case**: Applications with very large data volumes and high scalability and performance requirements.

### Conclusion

MongoDB offers a versatile solution for different use cases thanks to its various deployment models and flexible data structures. From simple single instance deployment for development purposes to complex sharded clusters for large, distributed systems, MongoDB can efficiently fulfill the requirements of modern applications. Knowledge of the basic terms and concepts as well as the various deployment models is crucial for the effective use of MongoDB in practice.


