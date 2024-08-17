
## MongoDB for .NET: Changing data - Update operations

In MongoDB, update operations are crucial for changing documents in a collection. These operations make it possible to find documents based on various criteria and make the desired changes. In .NET applications, MongoDB update operations are often performed by the MongoDB C# driver library. The basic update operations and their application in .NET are presented below.

### Basic update operations

#### 1. Simple update

The simplest form of update consists of finding a single document and updating it. This is done using the `UpdateOne` method.

-  Method**: `UpdateOne`
- **Description**: Updates the first document that matches the search criteria.

**Example:**

```csharp
using MongoDB.Driver;

// Create a MongoClient object
var client = new MongoClient(“mongodb://localhost:27017”);
var database = client.GetDatabase(“mydatabase”);
var collection = database.GetCollection<BsonDocument>(“mycollection”);

// Define the filter criterion
var filter = Builders<BsonDocument>.Filter.Eq(“name”, “John Doe”);

// Define the update operation
var update = Builders<BsonDocument>.Update.Set(“age”, 30);

// Execute the UpdateOne operation
var result = collection.UpdateOne(filter, update);
```
In this example, the age of the document with the name “John Doe” is changed to 30.

#### 2. Updating multiple documents
If several documents are to be updated, the UpdateMany method is used.

Method: UpdateMany
Description: Updates all documents that match the search criteria.
Example:


```csharp
using MongoDB.Driver;

// Create a MongoClient object
var client = new MongoClient(“mongodb://localhost:27017”);
var database = client.GetDatabase(“mydatabase”);
var collection = database.GetCollection<BsonDocument>(“mycollection”);

// Define the filter criterion
var filter = Builders<BsonDocument>.Filter.Eq(“status”, “inactive”);

// Define the update operation
var update = Builders<BsonDocument>.Update.Set(“status”, “active”);

// Execute the UpdateMany operation
var result = collection.UpdateMany(filter, update);

```

In this example, the status of all documents with the status “inactive” is changed to “active”.

#### 3. Update only the first document found
The FindOneAndUpdate method finds a document and updates it in one step.

Method: FindOneAndUpdate
Description: Finds a document, updates it and returns the original or updated document.

```csharp
using MongoDB.Driver;

// Create a MongoClient object
var client = new MongoClient(“mongodb://localhost:27017”);
var database = client.GetDatabase(“mydatabase”);
var collection = database.GetCollection<BsonDocument>(“mycollection”);

// Define the filter criterion
var filter = Builders<BsonDocument>.Filter.Eq(“name”, “Jane Doe”);

// Define the update operation
var update = Builders<BsonDocument>.Update.Inc(“age”, 1);

// Execute the FindOneAndUpdate operation
var updatedDocument = collection.FindOneAndUpdate(filter, update);

```

In this example, the age of the document with the name “Jane Doe” is increased by 1 and the updated document is returned.

### 4. update with conditions
The update method allows you to perform conditional updates, for example with update operators such as $set, $unset, $inc etc.

Operators:
“$set": Sets the value of a field.
“$unset": Removes a field.
“$inc": Increases the value of a numeric field.

```csharp
using MongoDB.Driver;

// Create a MongoClient object
var client = new MongoClient(“mongodb://localhost:27017”);
var database = client.GetDatabase(“mydatabase”);
var collection = database.GetCollection<BsonDocument>(“mycollection”);

// Define the filter criterion
var filter = Builders<BsonDocument>.Filter.Eq(“name”, “Alice”);

// Define the update operation
var update = Builders<BsonDocument>.Update
    .Set(“status”, “active”)
    .Inc(“age”, 1);

// Execute the UpdateOne operation
var result = collection.UpdateOne(filter, update);

```

In this example, the status of the document with the name “Alice” is set to “active” and the age is increased by 1.

