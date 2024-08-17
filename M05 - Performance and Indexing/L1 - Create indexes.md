
## MongoDB for .NET training: Creating indexes

Indexes are an important part of database optimization and management. In MongoDB, indexes enable fast search and data access optimization. In this course we will cover the importance and benefits of indexes and how to create simple and complex indexes in MongoDB.

### Meaning and benefits of indexes

Indexes are data structures that speed up the search for data in a database. They act like a table of contents in a book and help to find specific data records efficiently.

#### Advantages of indexes

1. **Faster queries**: Indexes speed up data retrieval by limiting the search to a smaller data set.
2 **Optimize query performance**: They improve the performance of searches, sorts and joins.
3 **Reduce database load**: By using indexes, less data is searched, reducing the load on the database.

#### Examples of index usage

- **Search queries**: When searching for a specific field, an index on that field can significantly speed up the search.
- **Sorting**: Indexes help to quickly sort results based on a specific field.

### Creating simple and complex indexes

#### Creating simple indexes

A simple index is created on a single field of a collection. This is the most basic form of index and is used for frequently queried fields.

**Example: Creating an index on a single field**

```csharp
using MongoDB.Bson;
using MongoDB.Driver;

var client = new MongoClient(“mongodb://localhost:27017”);
var database = client.GetDatabase(“exampleDB”);
var collection = database.GetCollection<BsonDocument>(“exampleCollection”);

// Creation of a simple index on the “name” field
var indexKeysDefinition = Builders<BsonDocument>.IndexKeys.Ascending(“name”);
collection.Indexes.CreateOne(new CreateIndexModel<BsonDocument>(indexKeysDefinition));
```

#### Creation of complex indexes
Complex indexes can be based on several fields or fulfill special requirements. These include composite indexes, unique indexes and multi-value indexes.

Composite indexes: A compound index is created on multiple fields to optimize queries that use multiple fields simultaneously.
Example: Creating a compound index on the fields “name” and “age”

```csharp
var indexKeysDefinition = Builders<BsonDocument>.IndexKeys
    .Ascending(“name”)
    .Ascending(“age”);
collection.Indexes.CreateOne(new CreateIndexModel<BsonDocument>(indexKeysDefinition));
```

Unique indexes: A unique index ensures that no two documents in the index have the same value for the indexed field.

Example: Creating a unique index on the “email” field

```csharp
var indexKeysDefinition = Builders<BsonDocument>.IndexKeys.Ascending(“email”);
var indexOptions = new CreateIndexOptions { Unique = true };
collection.Indexes.CreateOne(new CreateIndexModel<BsonDocument>(indexKeysDefinition, indexOptions));

```

Multivalued indexes: A multi-valued index is used to access arrays within documents and can be useful for queries that search array elements.

Example: Creating a multivalued index on the “tags” field

```csharp
var indexKeysDefinition = Builders<BsonDocument>.IndexKeys
    .Ascending(“tags”);
collection.Indexes.CreateOne(new CreateIndexModel<BsonDocument>(indexKeysDefinition));

```

