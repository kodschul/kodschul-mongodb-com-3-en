
## MongoDB for .NET: Deleting data - Delete operations

In MongoDB, data can be deleted in various ways. These operations are important for removing data that is no longer required or obsolete from your database. The various methods for deleting data in MongoDB and how they can be used in a .NET application are described below.

### Basic delete operations in MongoDB

MongoDB provides several methods for deleting documents in a collection. The main methods are:

#### 1. `DeleteOne`

The `DeleteOne` method is used to delete a single document that matches the specified filter condition. If several documents fulfill the condition, only the first document found is deleted.

- **Syntax**: `DeleteOne(FilterDefinition<T> filter)`

-  Example**: Deleting a document whose `name` field has the value “John Doe”.

```csharp
using MongoDB.Driver;

// Create an instance of the MongoClient
var client = new MongoClient(“mongodb://localhost:27017”);

// Select the database and the collection
var database = client.GetDatabase(“mydatabase”);
var collection = database.GetCollection<BsonDocument>(“mycollection”);

// Create a filter
var filter = Builders<BsonDocument>.Filter.Eq(“name”, “John Doe”);

// Delete a document
var result = collection.DeleteOne(filter);
Console.WriteLine($“Number of deleted documents: {result.DeletedCount}”);
```

### 2. DeleteMany
The DeleteMany method is used to delete all documents that match the specified filter condition. This method may delete several documents.

Syntax: DeleteMany(FilterDefinition<T> filter)

Example: Delete all documents whose status field has the value “inactive”.

```csharp
using MongoDB.Driver;

// Create an instance of the MongoClient
var client = new MongoClient(“mongodb://localhost:27017”);

// Select the database and the collection
var database = client.GetDatabase(“mydatabase”);
var collection = database.GetCollection<BsonDocument>(“mycollection”);

// Create a filter
var filter = Builders<BsonDocument>.Filter.Eq(“status”, “inactive”);

// Delete multiple documents
var result = collection.DeleteMany(filter);
Console.WriteLine($“Number of deleted documents: {result.DeletedCount}”);

```

### Important considerations
Filter criteria: The filter criteria determine which documents are deleted. Be careful with the filter conditions to avoid unintentional deletion.

Transactions: In MongoDB, you can use transactions to ensure that multiple delete operations are performed atomically. This is especially important if you want to ensure that all deletes are either completed or not performed at all.

Indexing: Ensure that the fields used in the filter criteria are indexed to improve the performance of delete operations.

