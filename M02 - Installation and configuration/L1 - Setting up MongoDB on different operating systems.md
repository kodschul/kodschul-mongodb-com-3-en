
## MongoDB: Differences between Windows and Linux

MongoDB is a popular NoSQL database that can be operated on various operating systems such as Windows and Linux. However, there are some differences in installation, configuration and administration between these operating systems. This guide compares the installation processes and configuration differences as well as a step-by-step guide to installing and initially configuring MongoDB on both systems.

### Comparison of the installation processes on different operating systems

#### Windows

1 **Download the installer**: MongoDB provides an MSI installer for Windows, which can be downloaded from the official MongoDB website.
2 **Installation**: The MSI installer guides the user through a graphical installation, including selecting the installation directory and configuring the MongoDB service.
3 **Service Management**: MongoDB is installed as a Windows service and can be controlled via the service management (services.msc) or the command line (sc.exe).

#### Linux

1 **Add repository**: Add the MongoDB repository to your package management (e.g. APT for Debian/Ubuntu, YUM for CentOS/RHEL).
2 **Installation via package manager**: Install MongoDB with the appropriate package manager command (e.g. `sudo apt-get install mongodb`).
3 **Service management**: MongoDB is installed as a system service and can be controlled with systemd (`systemctl start mongod`) or init.d (`service mongod start`).

### Important differences in the configuration

#### Configuration file

-  Windows**: The configuration file is typically located in the installation directory, e.g. `C:\Program Files\MongoDB\Server\<version>\bin\mongod.cfg`.
-  Linux**: The configuration file is usually located under `/etc/mongod.conf`.

#### Paths and directories

-  Windows**: By default, data is stored in `C:\Program Files\MongoDB\Server\<version>\data` and logs in `C:\Program Files\MongoDB\Server\<version>\log`.
-  Linux**: By default, data is stored in `/var/lib/mongodb` and logs in `/var/log/mongodb`.

#### Service control

-  Windows**: Services can be controlled via the service administration or commands such as `net start MongoDB`.
-  Linux**: Services are controlled via systemd (`systemctl start mongod`) or init.d (`service mongod start`).

### Step-by-step installation

#### Windows

1. **Download**: Download the MongoDB installer from the official website.
2. **Installation**: Run the installer and follow the instructions. Select the full installation and set up the MongoDB service.
3 **Configuration**: Edit the `mongod.cfg` file to make the desired configuration settings.
4 **Starting the service**: Start MongoDB via the service management or the command line.

#### Linux (Ubuntu)

1. **Add repository**:
    ```sh
    wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
    echo “deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.4 multiverse” | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
    sudo apt-get update
    ```
2. **Installation**:
    ```sh
    sudo apt-get install -y mongodb-org
    ```
3. **Configuration**: Edit the `/etc/mongod.conf` file to make the desired configuration settings.
4. **Start the service**:
    ```sh
    sudo systemctl start mongod
    sudo systemctl enable mongod
    ```

### Initial configuration and starting the MongoDB instance

#### Windows

1 **Edit configuration**: Open the `mongod.cfg` file and make adjustments (e.g. data directory, port, authentication).
2 **Start service**: Start the MongoDB service via the service administration or the command line.
3 **Test connection**: Use the MongoDB shell (`mongo.exe`) to connect to your MongoDB instance and make sure it is working properly.

#### Linux

1 **Edit configuration**: Edit the `/etc/mongod.conf` file and make adjustments (e.g. data directory, port, authentication).
2 **Start service**: Start the MongoDB service and activate it for automatic start.
3 **Test connection**: Use the MongoDB shell (`mongo`) to connect to your MongoDB instance and make sure it is working properly.

This guide provides an overview of the differences and similarities in installing and configuring MongoDB on Windows and Linux, as well as step-by-step instructions for installation and initial configuration.


