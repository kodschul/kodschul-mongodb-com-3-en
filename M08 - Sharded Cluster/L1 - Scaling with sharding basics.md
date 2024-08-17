
## MongoDB for .NET: Scaling with sharding - basics

Sharding is a method of horizontally scaling databases by distributing data across multiple servers (shards) to distribute the load and increase performance. MongoDB, a popular NoSQL database, uses sharding to efficiently manage large amounts of data. The following introduces the basic concepts of sharding in MongoDB.

### Basic concepts of sharding

#### 1. Shard

A shard is a single instance or a cluster of instances that contain a part of the overall database. Each shard manages a specific part of the data, which is determined by the shard key.

-  Example**: In an e-commerce application, one shard could manage the data of customers with IDs from 1 to 1,000,000, while another shard manages the data of customers with IDs from 1,000,001 to 2,000,000.

#### 2. Shard key

The shard key is a field or a combination of fields that is used to distribute the data to the shards. The choice of shard key is crucial for the performance and efficiency of sharding, as it determines how the data is distributed to the shards.

- **Example**: In a user data management application, the `user_id` field could be used as the shard key.

#### 3. Chunk

A chunk is a contiguous data record area that is stored on a shard. MongoDB automatically splits data into chunks based on the shard key. Each chunk contains a subset of the data that corresponds to a specific range of the shard key.

- **Example**: A chunk could contain all data for `user_id` values between 1,000,000 and 1,000,100.

#### 4. Balancer

The balancer is a background process in MongoDB that ensures that chunks are distributed evenly across the shards. The balancer moves chunks between shards to distribute the load evenly and ensure that no shards are overloaded.

-  Example**: If one shard is overloaded and another shard is underloaded, the balancer can move chunks from the overloaded shard to the underloaded shard.

#### 5. Config Server

Config Server stores metadata about the sharding system, including the distribution of chunks and the configuration of the shards. It is crucial for the management of the sharding system and enables coordinated management of data distribution.

- **Example**: The config servers store information about which shard contains which chunks in order to quickly identify the correct shard in response to requests.

### Sharding in MongoDB: Implementation steps

#### 1. Setting up the shards

Shards must first be set up and configured. This can be done by deploying MongoDB instances or clusters that will act as shards.

#### 2. Configuring the Config Server

The config servers need to be set up to store the metadata for the sharding system. This is normally done in a cluster of at least three Config Servers for redundancy.

#### 3. Creating and configuring sharding

Sharding is activated on a collection by defining a shard key. MongoDB then automatically distributes the data based on this key field.

- **Example**: To enable sharding for the collection `orders`, the following command could be used:

  ```javascript
  sh.shardCollection(“mydb.orders”, { “order_id”: 1 });
  ```

#### 4. Monitoring and management
Once sharding has been implemented, the system must be monitored to ensure that the balancer is working correctly and the data is evenly distributed. It is important to regularly check the performance and load distribution and make adjustments if necessary.

