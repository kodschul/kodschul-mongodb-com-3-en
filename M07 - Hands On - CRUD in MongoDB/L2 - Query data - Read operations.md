
## MongoDB for .NET: Querying data - Read operations

MongoDB is a powerful NoSQL database that is document-oriented and offers flexible data structures. In a .NET application, you can use the MongoDB C# drivers to query data and perform read operations. This guide provides an overview of the common read operations in MongoDB and how you can perform them with .NET.

### Basics of read operations

MongoDB supports several types of read operations that allow you to read data from your collections. The basic read operations include retrieving documents, filtering results and sorting data.

#1 Connect to the MongoDB database

Before you can query data, you need to connect to your MongoDB database. This is typically done via the `MongoClient` object.

```csharp
using MongoDB.Bson;
using MongoDB.Driver;

// Creating a MongoClient object
var client = new MongoClient(“mongodb://localhost:27017”);

// Access to the database
var database = client.GetDatabase(“mydatabase”);

// Access to the collection
var collection = database.GetCollection<BsonDocument>(“mycollection”);
```

### 2. query all documents
To retrieve all documents from a collection, use the Find method without a filter.

```csharp
var allDocuments = collection.Find(new BsonDocument()).ToList();

// Output of the documents
foreach (var document in allDocuments)
{
    Console.WriteLine(document.ToJson());
}

```

### 3. filter documents according to criteria
To filter documents according to certain criteria, use filter builder methods. Here is an example of how to query documents with a specific field value.

```csharp
var filter = Builders<BsonDocument>.Filter.Eq(“fieldname”, “value”);
var filteredDocuments = collection.Find(filter).ToList();

// Output of the filtered documents
foreach (var document in filteredDocuments)
{
    Console.WriteLine(document.ToJson());
}

```

### 4. sorting documents
You can sort results by specifying a sort order. Here is an example of how to sort documents by a specific field.

```csharp
var sort = Builders<BsonDocument>.Sort.Ascending(“fieldname”);
var sortedDocuments = collection.Find(new BsonDocument()).Sort(sort).ToList();

// Output of the sorted documents
foreach (var document in sortedDocuments)
{
    Console.WriteLine(document.ToJson());
}

```

### 5. Query individual documents
To retrieve a single document based on a filter criterion, use Find with a restriction to the first document found.

```csharp
var singleDocument = collection.Find(filter).FirstOrDefault();

// Output of the document
if (singleDocument != null)
{
    Console.WriteLine(singleDocument.ToJson());
}
else
{
    Console.WriteLine(“Document not found.”);
}

```

### 6. retrieve documents with projection
Projection allows you to retrieve only certain fields from documents. Here is an example of how to return only certain fields.

```csharp
var projection = Builders<BsonDocument>.Projection.Include(“fieldname”);
var documentsWithProjection = collection.Find(new BsonDocument()).Project(projection).ToList();

// Output of the projected documents
foreach (var document in documentsWithProjection)
{
    Console.WriteLine(document.ToJson());
}

```

