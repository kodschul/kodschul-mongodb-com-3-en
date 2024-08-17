
## MongoDB for .NET Training: Hands-On: Installing a Replica Set

### Practical exercise for setting up a replica set

A replica set in MongoDB provides high availability and redundancy by replicating data to multiple nodes. In this practical exercise, we will set up and configure a replica set step by step.

#### Step-by-step guide

**Prerequisites**:
- Three or more servers or virtual machines (VMs) for the MongoDB instances.
- MongoDB installed on all participating servers.
- Network access between the servers.

#### 1. Configuration of the MongoDB instances

On each server, you must configure the MongoDB instance so that it becomes part of a replica set. Edit the `mongod.conf` file (by default under `/etc/mongod.conf` on Linux or in the installation directory on Windows) and add the following configurations:

```yaml
replication:
  replSetName: “rs0”
```

#### 2. Starting the MongoDB instances
Start each MongoDB instance with the updated configuration:

Linux:
```sh
sudo systemctl restart mongod
```

Windows:
```sh
net stop MongoDB
net start MongoDB
```

#### 3. Initializing the replica set
Log in to one of the MongoDB instances and initialize the replica set. Open the MongoDB shell (mongo) and execute the following commands:

```js
// Connect to the primary instance
rs.initiate(
  {
    _id: “rs0”,
    members: [
      { _id: 0, host: “server1:27017” },
      { _id: 1, host: “server2:27017” },
      { _id: 2, host: “server3:27017” }
    ]
  }
);
```
Replace server1, server2 and server3 with the actual host names or IP addresses of the servers.

#### 4. Check the replication
Check the status of the replica set to ensure that all members are correctly configured and operational:

```js
rs.status();
```


```yaml
replication:
  replSetName: “rs0”
```

