
## Getting started with the MongoDB Shell

The MongoDB Shell is an interactive tool used to interact with MongoDB databases. In this training we will go through the basic steps to get familiar with the MongoDB Shell and perform basic operations.

#1 Connect to the MongoDB Shell

To use the MongoDB Shell, you must first connect to your MongoDB server. The shell is normally started via the command line.

-  Command**: `mongo`
-  Connection to a specific server**: `mongo <hostname>:<port>`

Example:
```bash
mongo localhost:27017
```

This establishes a connection to the MongoDB server on your local computer on the standard port 27017.

### 2. basic operations
### 2.1 Display databases
To display all available databases, use the show dbs command:

```js
show dbs

```

This command lists all databases that are available on the MongoDB server.

### 2.2 Selecting a database
To work with a specific database, use the use command:

```js
use myDatabase

```

This command selects the database myDatabase. If the database does not exist, it will be created as soon as you save data in it.

### 2.3 Displaying a collection
You can display the available collections within a database:

```js
show collections

```

### 2.4 Inserting documents
To insert a new document into a collection, use the insertOne or insertMany method:

```js
db.myCollection.insertOne({ name: “Alice”, age: 30 })

```

Example for multiple documents:

```js
db.myCollection.insertMany([
  { name: “Bob”, age: 25 },
  { name: “Carol”, age: 28 }
])

```

### 2.5 Query documents
To retrieve documents from a collection, use the find method:

```js
db.myCollection.find()
```

To make the output more readable, you can use pretty():

```js
db.myCollection.find().pretty()
```

### 2.6 Updating documents
To update documents, use the updateOne or updateMany method:

```js
db.myCollection.updateOne(
  { name: “Alice” },
  { $set: { age: 31 } }
)
```

### 2.7 Deleting documents
To delete documents, use the deleteOne or deleteMany method:

```js
db.myCollection.deleteOne({ name: “Alice” })
```

### 3. Working with the MongoDB Shell in .NET
In .NET applications, you can manage the MongoDB database via the MongoDB .NET Driver API. Here are some basic steps for connecting and interacting with MongoDB in .NET:

Installing the MongoDB .NET Driver:

Add the MongoDB .NET Driver to your project:

```bash
dotnet add package MongoDB.Driver
```

Establish a connection to MongoDB:

Sample code to establish a connection and perform basic operations:

```js
using MongoDB.Driver;

var client = new MongoClient(“mongodb://localhost:27017”);
var database = client.GetDatabase(“myDatabase”);
var collection = database.GetCollection<BsonDocument>(“myCollection”);

// Insert a document
var document = new BsonDocument { { “name”, “Alice” }, { “age”, 30 } };
collection.InsertOne(document);

// Query documents
var documents = collection.Find(new BsonDocument()).ToList();

```

