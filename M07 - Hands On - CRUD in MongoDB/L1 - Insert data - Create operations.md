
## MongoDB for .NET: Insert data - Create operations

MongoDB is a document-oriented NoSQL database that is frequently used in .NET applications. The basic operation for adding data in MongoDB is the create operation. This operation is used to insert new documents into a collection. The basic methods and concepts for inserting data into MongoDB with .NET are described below.

### Prerequisites

To use MongoDB in a .NET application, you need the MongoDB.Driver library. This can be integrated into your .NET project via NuGet.

```bash
dotnet add package MongoDB.Driver
```

### 1. establish a connection to the MongoDB database
Before you can insert data, you must establish a connection to the MongoDB database and select a collection.

```csharp
using MongoDB.Driver;

var connectionString = “mongodb://localhost:27017”;
var client = new MongoClient(connectionString);
var database = client.GetDatabase(“mydatabase”);
var collection = database.GetCollection<BsonDocument>(“mycollection”);

```

### 2nd simple create operation: Inserting a single document
To insert a single document into the collection, use the InsertOne() method.

```csharp
using MongoDB.Bson;
using MongoDB.Driver;

var document = new BsonDocument
{
    { “Name”, “Alice” },
    { “Age”, “30” },
    { “City”, “New York” }
};

collection.InsertOne(document);

```

In this example, a document with the fields “Name”, “Age” and “City” is inserted into the collection.

### 3. insert multiple documents
To insert several documents at the same time, use the InsertMany() method.

```csharp
using MongoDB.Bson;
using MongoDB.Driver;

var documents = new List<BsonDocument>
{
    new BsonDocument { { “Name”, “Bob” }, { “Age”, 25 }, { “City”, “Los Angeles” } },
    new BsonDocument { { “Name”, “Charlie” }, { “Age”, 35 }, { “City”, “Chicago” } }
};

collection.InsertMany(documents);

```

In this example, two documents are inserted into the collection at once.

### 4. inserting data with a typed model
Instead of raw BSON documents, you can also use a typed model to insert data.

```csharp
using MongoDB.Bson.Serialization.Attributes;

public class Person
{
    [BsonId]
    public ObjectId Id { get; set; }

    public string Name { get; set; }
    public int Age { get; set; }
    public string City { get; set; }
}

var person = new Person
{
    Name = “David”,
    Age = 40,
    City = “San Francisco”
};

collection.InsertOne(person);

```

In this example, a document is created as an instance of the Person class and inserted into the collection.

### 5. error handling for create operations
It is important to handle errors that may occur when inserting documents, especially when working with large amounts of data or in production environments.

```csharp
try
{
    collection.InsertOne(document);
}
catch (MongoWriteException ex)
{
    // Error handling
    Console.WriteLine($“Error inserting the document: {ex.Message}”);
}

```

