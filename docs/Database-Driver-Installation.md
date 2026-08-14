# Database Driver Installation

The following relates to NoSQL & Relational Databases only, meaning this can be ignored if either RocksDB/SQLite are being used (both included in TaskTide [release zips](https://github.com/BrenKenna/TaskTide/releases)). The JDBC drivers for databases like Postgres, MySQL, MariaDB etc can downloaded from preferred source or from the collection maintained by JetBrains [linked here](https://www.jetbrains.com/datagrip/jdbc-drivers/#), and an example installaion is [provided here](/Database-Driver-Installation.md#1-install-required-relational-database-driver).

<br>
<br>

A collection of Jakarta-NoSQL database drivers have been included within TaskTide. These are MongoDB and CouchDB for DocumentTemplate, Cassandra for ColumnTemplate, Redis and DynamoDB for KeyValueTemplate with their use is [described here](/Database-Driver-Installation.md#2-using-pre-packaged-nosql-database-driver). In the event that other database drivers are required see the [following guide](Database-Driver-Installation.md#3-using-another-nosql-database-driver).
<br>


## 1). Install Required Relational Database Driver

The following instructions are relative to the root folder of the  [release zips](https://github.com/BrenKenna/TaskTide/releases) which occur "tasktide-< VERSION >". Adjust upper path references according to your installation where appropriate. Since the MySQL driver is provided within the TaskTide release zip, the following details using Microsoft SQL Server. A similar process can be used for other relational databases.
<br>

    1. Download the required JDBC, if not known they are available from JetBrains at [this link](https://download.jetbrains.com/idea/jdbc-drivers/web/mssql-12.8.1.zip) which downloads version 12.8.1. Then place that jar file into the "Tasktide-< VERSION >/lib" folder.
    2. Optionally remove the unused <i>tasktide-< VERSION >/lib/"mysql-connector-j-8.0.33.jar</i>".
    3. Optionally, remove the unused JNoSQL JARs from "tasktide-< VERSION >/lib/".
    4. Adjust Microsoft SQL Server [template config file](configs/microsoft-sql-config.properties) according to your deployment.

<br>
<br>

## 2). Using Pre-Packaged NoSQL-Database Driver

The pre-packaged NoSQL databases are couchDB, MongoDB, ArangoDB, couchBase, DynamoDB, Cassandra and Redis. The instructions below can adapted for [preferred database](https://github.com/eclipse-jnosql/jnosql-databases).
<br>

    1. Optionally, remove the JNoSQL JARs. Since couchDB uses the [DocumentTemplate](https://github.com/eclipse-jnosql/jnosql-databases?tab=readme-ov-file#couchdb). This would be the Graph, KeyValue and Column jars Communication-Column/Key-Value/Graph.jar, and Mapping JNoSQL JARs.
    2. Then optionally delete the unused JNoSQL Cassandra, ArangoDB, CouchBase, DynamoDB, MongoDB, and JNoSQL JARs.

<br>

## 3). Using Another NoSQL-Database Driver

An example few NoSQL databases were packaged with TaskTide for unit testing purposes. These are couchDB, MongoDB, ArangoDB, couchBase, DynamoDB, Cassandra and Redis. It is important to note that TaskTide was designed for ETL scale-outs which supported < THESE RESEARCH PAPERS >, where [couchDB/DynamoDB](https://github.com/BrenKenna/pyanamo) were used. Since these databases all performed really well. The choice in the backend is considered "<i>dealers choice</i>"/what is more conveniently deployed, because TaskTide's development did not want constrain this area.
<br>

With the jnosql-communication, and jnosql-mapping JARs packaged into TaskTide. The required driver must be installed, as fetching the JAR from [Maven Central](https://mvnrepository.com/artifact/org.eclipse.jnosql.databases/jnosql-mongodb/1.1.6) will not include the dependancies that that driver uses. While an example is provided for [Oracle NoSQL](https://github.com/eclipse-jnosql/jnosql-databases/tree/main?tab=readme-ov-file#oracle-nosql), building from source with Gradle/Maven is outside the scope of this documentation and is not supported.
<br>
<br>

```bash
# Fetch the pom.xml
curl -so pom.xml https://repo1.maven.org/maven2/org/eclipse/jnosql/databases/jnosql-oracle-nosql/1.1.9/jnosql-oracle-nosql-1.1.9.pom

# Fetch dependancies: Oracle's Driver is nosqldriver-5.4.17.jar
mvn dependency:copy-dependencies -DoutputDirectory=./oracle

# Move all jars to lib
mv ./oracle/*jars tasktide-0.9.0/lib/

# Fetch the JNoSQL Oracle Driver
curl -so tasktide-0.9.0/lib/jnosql-oracle-nosql-1.1.9.jar https://repo1.maven.org/maven2/org/eclipse/jnosql/databases/jnosql-oracle-nosql/1.1.9/jnosql-oracle-nosql-1.1.9.jar
```
<br>