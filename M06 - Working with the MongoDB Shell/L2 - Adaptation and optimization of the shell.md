
## MongoDB for .NET: customization and optimization of the shell

MongoDB is a popular NoSQL database that offers a flexible schema structure and powerful query functions. The MongoDB shell (`mongo`) is a powerful tool for interacting with the database. In this course we will look at customizing and optimizing the MongoDB shell to improve efficiency and usability.

### Customizing the MongoDB shell

#### 1. use of configuration files

MongoDB allows the use of configuration files to customize the shell environment. These files can contain, for example, user-defined functions or variables that are loaded each time the shell is started.

-  Example**: A configuration file `mongo_config.js` could define user-defined functions.

```javascript
// mongo_config.js
function log(msg) {
  print('Log: ' + msg);
}

db.customCollection = db.getCollection('myCollection');
```

To load this configuration, start the shell with :


```sh
mongo --eval “load(‘mongo_config.js’)”
```

### 2. use of shell scripts
Shell scripts are a great way to automate repetitive tasks. You can create scripts that contain multiple MongoDB commands to simplify complex processes.

Example: A setup.js script to create indexes and initial data.


```javascript
// setup.js
db.myCollection.createIndex({ name: 1 });
db.myCollection.insertMany([
  { name: 'Alice', age: 30 },
  { name: 'Bob', age: 25 }
]);

```

Execute the script in the shell:

```sh
mongo setup.js
```

### Optimization of the MongoDB shell
1. use of aggregation pipelines
The aggregation pipeline in MongoDB enables complex data analyses and transformations. By using the pipeline, you can perform computationally intensive operations on the database side to improve the performance of the application.

Example: An aggregation pipeline to calculate the average age.

```javascript
db.myCollection.aggregate([
  { $group: { _id: null, averageAge: { $avg: “$age” } } }
]);

```

### 2. indexing to increase performance
Indexes are crucial for optimizing queries in MongoDB. By creating suitable indexes, you can significantly improve the performance of queries.

Example: Creating an index on the name field.

```javascript
db.myCollection.createIndex({ name: 1 });
```

Check the indexes used with :

```javascript
db.myCollection.getIndexes();
```

### 3. use of profiling tools
MongoDB provides profiling tools to identify and optimize slow queries. The profiler can be used to obtain detailed information about the queries performed.

Example: Activate the profiler level to 1 (record all slow queries).

```javascript
db.setProfilingLevel(1, 100); // Profiling for queries that take longer than 100ms

```

Queries the profiling data:

```javascript
db.system.profile.find().pretty();

```

