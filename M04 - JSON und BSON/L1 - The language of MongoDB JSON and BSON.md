
## MongoDB for .NET training: Introduction to the syntax

MongoDB is a document-oriented NoSQL database that uses JSON-like documents to store data. When working with MongoDB in a .NET application, it is important to understand the basics of syntax, especially JSON syntax and how it differs from BSON (Binary JSON). These concepts are crucial for working efficiently with MongoDB and the .NET MongoDB driver library.

### Basics of JSON syntax

JSON (JavaScript Object Notation) is a lightweight data format commonly used for transferring data between a server and a web client. JSON is easy to read and write and is supported by many programming languages.

#### JSON basics

- **Objects**: JSON objects are unordered collections of key-value pairs. They begin and end with curly brackets `{}`.
-  Arrays**: JSON arrays are ordered lists of values enclosed in square brackets `[]`.
- **Values**: JSON values can be strings, numbers, booleans, arrays, objects or `null`.

#### Example of a JSON document

```json
{
  “name": ‘Alice’,
  “age": 30,
  “isActive": true,
  “skills“: [”C#”, ‘MongoDB’, ‘ASP.NET’],
  “address": {
    “street": ‘123 Main St’,
    “city": ”Anytown”
  }
}
```

In this example, the JSON document contains various data types, including strings, numbers, booleans, arrays and nested objects.

### Differences between JSON and BSON
BSON (Binary JSON) is a binary format used by MongoDB to store and transfer data. While BSON has many similarities with JSON, there are some important differences that are relevant for working with MongoDB.

#### Differences in detail
1. binary format

JSON: Text-based and human-readable.
BSON: Binary format that is optimized for machines. It is not directly readable, but can be processed by MongoDB tools.
2. data types

JSON: Supports basic data types such as String, Number, Boolean, Array, Object and null.
BSON: Extends the data types of JSON with additional types such as Date, Binary, ObjectId, Regular Expression and Code.
3. storage format

JSON: Is less efficient in size and can take up more storage space as it is text-based.
BSON: Is more compact and offers more efficient storage through the use of binary data structures.
4. access and processing

JSON: Easy to parse and process as it is text-based. Many programming languages offer native support for JSON.
BSON: Used internally by MongoDB and optimized for fast read and write operations. BSON data can be processed by the MongoDB drivers in various programming languages.

#### Example of a BSON document
As BSON is a binary format, it does not look like readable text, unlike JSON. BSON data is typically managed directly by MongoDB clients and drivers.

