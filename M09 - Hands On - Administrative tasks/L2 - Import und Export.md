
## MongoDB for .NET: Migrating data - import and export

Migrating data to and from MongoDB is a common task when managing databases. MongoDB provides various tools and methods for importing and exporting data to facilitate migration between different environments or databases. This guide describes the basic concepts and commands for importing and exporting data in MongoDB.

### Importing data

Importing data into MongoDB can be done using the `mongoimport` tool. This tool makes it possible to import data from JSON, CSV or TSV files into a MongoDB database.

#### 1. Importing JSON data

To import JSON data, use the following command:

```bash
mongoimport --db <database name> --collection <collection name> --file <file path> --jsonArray
```
--db: Name of the target database.
--collection: Name of the collection in the target database.
--file: Path to the file to be imported.
--jsonArray: Specifies that the file contains an array of JSON documents.

```bash
mongoimport --db mydatabase --collection mycollection --file data.json --jsonArray

```
### 2. importing CSV data
To import CSV data, use the following command:

```bash
mongoimport --db <database name> --collection <collection name> --type csv --headerline --file <file path>

```
--type csv: Specifies that the file is in CSV format.
--headerline: Specifies that the first line of the CSV file contains the field names.

```bash
mongoimport --db mydatabase --collection mycollection --type csv --headerline --file data.csv
```

### Exporting data
Data can be exported from MongoDB using the mongoexport tool. This tool makes it possible to export data from MongoDB to JSON or CSV files.

1. exporting data as JSON
To export data as JSON, use the following command:

```bash
mongoexport --db <database name> --collection <collection name> --out <file path> --jsonArray

```

--db: Name of the database to be exported from.
--collection: Name of the collection to be exported from.
--out: Path to the target file.
--jsonArray: Specifies that the data will be exported as an array of JSON documents.


```bash
mongoexport --db mydatabase --collection mycollection --out data.json --jsonArray


```

2. exporting data as CSV
To export data as CSV, use the following command:

```bash
mongoexport --db <database name> --collection <collection name> --type csv --out <file path> --fields <field name>


```

--type csv: Specifies that the data is exported in CSV format.
--fields: A comma-separated list of the field names to be exported.

```bash
mongoexport --db mydatabase --collection mycollection --type csv --out data.csv --fields name,age,address

```

### Tips for data migration
Data validation: Check the integrity and accuracy of the data after importing or exporting.
Performance: For large amounts of data, you can perform the import or export in batches to improve performance.
Backup: Create a backup of your database before migrating data to avoid data loss.

