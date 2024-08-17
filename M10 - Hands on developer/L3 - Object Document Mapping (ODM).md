
## MongoDB for .NET: Object-document mapping (ODM)

Object-document mapping (ODM) is a concept that enables the mapping of objects in an object-oriented programming language to documents in a document-oriented database such as MongoDB. In the .NET world, this mapping is supported by special libraries and tools that facilitate interaction with MongoDB.

### What is object-document mapping (ODM)?

ODM is a technique that allows developers to work with database documents in a way that is consistent with the principles of object-oriented programming. It translates between the object-oriented world (classes and objects) and the document-oriented world (documents in a NoSQL database).

### Advantages of ODM

1.  abstraction and simplification: ODM abstracts away the details of database interactions and allows developers to focus on business logic and data models.
2 **Type safety**: By using strongly typed classes, the integrity of the data structure is ensured and type errors are detected at development time.
3 **Automation**: ODM libraries automate many of the repetitive tasks such as inserting, retrieving and updating data, which increases productivity.

### MongoDB ODM for .NET

There are several ODM libraries available for .NET developers, but the most widely used is **MongoDB.Driver**. This library provides comprehensive functions for interacting with MongoDB and mapping .NET classes to MongoDB documents.

#### Example for the use of MongoDB.Driver

1 **Installation of the MongoDB.Driver package**

   To use MongoDB.Driver in a .NET project, the package must be installed. This can be done via NuGet:

   ```bash
   dotnet add package MongoDB.Driver
   ```

2 **Definition of a data model**

    Define a C# class that represents the structure of a MongoDB document. Each property of the class corresponds to a field in the document.

    ```csharp
    using MongoDB.Bson;
    using MongoDB.Bson.Serialization.Attributes;

    public class Person
    {
        [BsonId]
        public ObjectId Id { get; set; }

        [BsonElement(“name”)]
        public string Name { get; set; }

        [BsonElement(“age”)]
        public int Age { get; set; }
    }

    ```

    In this example, the Person class represents a document in the MongoDB database. The BsonId annotation identifies the Id field as the primary key, and the BsonElement annotations specify the names of the fields in the MongoDB documents.

3 **Connection to the MongoDB database and CRUD operations**

    Here is a simple example of how to connect to the database and perform CRUD operations using MongoDB.Driver:

    ```csharp
        using MongoDB.Driver;
        using System;
        using System.Threading.Tasks;

        class Program
        {
            private static IMongoCollection<Person> GetCollection()
            {
                var client = new MongoClient(“mongodb://localhost:27017”);
                var database = client.GetDatabase(“testdb”);
                return database.GetCollection<Person>(“people”);
            }

            static async Task Main(string[] args)
            {
                var collection = GetCollection();

                // Create a new document
                var person = new Person { Name = “John Doe”, Age = 30 };
                await collection.InsertOneAsync(person);

                // Retrieve a document
                var retrievedPerson = await collection.Find(p => p.Name == “John Doe”).FirstOrDefaultAsync();
                Console.WriteLine($“Name: {retrievedPerson.Name}, Age: {retrievedPerson.Age}”);

                // Updating a document
                var filter = Builders<Person>.Filter.Eq(p => p.Name, “John Doe”);
                var update = Builders<Person>.Update.Set(p => p.Age, 31);
                await collection.UpdateOneAsync(filter, update);

                // Delete a document
                await collection.DeleteOneAsync(p => p.Name == “John Doe”);
            }
        }

    ```

    In this example, a connection to the MongoDB database is established, a document is inserted, retrieved, updated and finally deleted.


