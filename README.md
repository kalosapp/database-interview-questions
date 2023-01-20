# Database Interview Questions

| Sl.No|  Questions       |
|------|------------------|
| 01. |[What is ACID Transaction?](#q-what-is-acid-transaction)|
| 02. |[What is CAP theorem?](#q-what-is-cap-theorem)|
| 03. |[Describe types of NoSQL databases?](#q-describe-types-of-nosql-databases)|
| 04. |[Differences between SQL and NoSQL?](#q-differences-between-sql-and-nosql)|
| 05. |[What is database replica?](#q-what-is-database-replica)|
| 06. |[What is Sharding?](#q-what-is-sharding)|
| 07. |[Explain dynamodb indexing](#q-explain-dynamodb-indexing)|

<br/>

## Q. ***What is ACID Transaction?***

ACID (Atomicity, Consistency, Isolation, Durability) is a set of properties that guarantee that database transactions are processed reliably.

***1. Atomicity:*** This property ensures that a transaction is treated as a single, indivisible unit of work. If any part of the transaction fails, the entire transaction is rolled back, and the database is left unchanged. This means that either all the changes made by the transaction are committed or none of them are.

***2.Consistency:*** This property ensures that a transaction brings the database from one valid state to another. This means that when a transaction starts, the database is in a consistent state and when it ends, the database is also in a consistent state. It guarantees that the database will not violate any integrity constraints like foreign key relationships.

***3.Isolation:*** This property ensures that concurrent transactions do not interfere with each other. This means that each transaction works on its own copy of the data, and it doesn't see the changes made by other transactions until they are committed. This ensures that the database will not return inconsistent data to the user

***4.Durability:*** This property ensures that once a transaction is committed, its effects are permanent and survive any subsequent crashes or power failures. It is typically implemented by writing the changes made by the transaction to disk.

ACID transactions are used to ensure data integrity and consistency in a database. It guarantees that the database will always be in a consistent state and that data is not lost or corrupted. ACID transactions are supported by most relational databases such as MySQL, PostgreSQL, and Oracle, and is a key feature for systems that need to maintain data integrity and consistency.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is CAP theorem?***

CAP theorem is a concept that states that it is impossible for a distributed system to simultaneously provide all three of the following guarantees:

***Consistency:*** All nodes in the system see the same data at the same time.

***Availability:*** Every request receives a response, without guarantee that it contains the most recent version of the data.

***Partition tolerance:*** The system continues to function despite arbitrary partitioning due to network failures.

The CAP theorem states that a distributed system can only guarantee two of these properties at the same time, not all three. It means that in a distributed system, you have to make a trade-off between consistency, availability, and partition tolerance.

A system that prioritizes consistency, such as a relational database, may become unavailable if a network partition occurs. A system that prioritizes availability, such as a NoSQL database, may return stale data if a network partition occurs. A system that prioritizes partition tolerance, such as a distributed file system, may sacrifice consistency and availability in the event of a network partition.

It is important to note that the CAP theorem does not mean that a distributed system cannot have all three properties, but that it cannot guarantee all three simultaneously under all conditions. The theorem is a way to understand the trade-offs that need to be made when designing a distributed system, and to choose an appropriate strategy depending on the needs of the application.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Describe types of NoSQL databases.***

NoSQL databases are a category of databases that do not use the traditional relational model and SQL language used by relational databases. They are designed to handle large amounts of unstructured and semi-structured data, and to scale horizontally.

Here are some of the most common types of NoSQL databases:

***Document databases:*** These databases store data in the form of documents, such as JSON or BSON, and allow for flexible and nested data structures. Examples of document databases include MongoDB, Couchbase, and RavenDB.

***Key-value databases:*** These databases store data as key-value pairs and are optimized for fast read and write operations. Examples of key-value databases include Redis and Riak.

***Column-family databases:*** These databases store data in column families and are optimized for fast read and write operations on large data sets. Examples of column-family databases include Apache Cassandra and HBase.

***Graph databases:*** These databases store data in the form of nodes and edges and are optimized for querying data with complex relationships. Examples of graph databases include Neo4j and OrientDB.

***Time-series databases:*** These databases are optimized for storing and querying time-stamped data and are commonly used for monitoring, logging and sensor data. Examples of time-series databases include InfluxDB and OpenTSDB.

***Object databases:*** These databases store data in the form of objects and have a close relationship to the object-oriented programming model. Examples of object databases include db4o and ZODB.

It's worth mentioning that some databases can have multiple characteristics, for example, MongoDB is a document-based database, but it also has support for graph data, and some databases can also have a hybrid approach, for example, a document-based database that also supports graph or relational data.
<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Differences between SQL and NoSQL?***

SQL (Structured Query Language) and NoSQL (Not only SQL) are two different types of databases that have different characteristics and are used for different purposes.

Here are the main differences between SQL and NoSQL databases:

Data model: SQL databases use a relational data model, where data is organized into tables with rows and columns and relationships between tables are defined by foreign keys. NoSQL databases, on the other hand, use a variety of data models such as document, key-value, graph, and column-family.

Schema: SQL databases have a fixed schema, meaning that the structure of the data must be defined in advance and cannot be changed easily. NoSQL databases, on the other hand, have a flexible schema, meaning that the structure of the data can be changed easily.

Query language: SQL databases use SQL as their query language, which is a standard language for querying relational databases. NoSQL databases, on the other hand, use a variety of query languages, some of which are specific to a particular database.

Scale-out: SQL databases are typically scaled vertically, meaning that they are scaled by adding more resources to a single server. NoSQL databases, on the other hand, are typically scaled horizontally, meaning that they are scaled by adding more servers to a cluster.

Use cases: SQL databases are best suited for structured, transactional data and applications that require complex queries and joins. NoSQL databases, on the other hand, are best suited for unstructured, non-transactional data and applications that require high scalability and low latency.

Performance: SQL databases are best suited for complex queries and transactional operations and can handle large number of concurrent operations. NoSQL databases are best suited for high write and read loads and can handle large number of concurrent operations and big data

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is database replica?***

A replica is a copy of a database or other data storage system that is kept in sync with the original. Replicas are used to increase the availability, scalability and fault-tolerance of a system by providing a backup that can take over in case of failure.

There are different types of replication that can be used depending on the specific needs of the application and the data storage system being used.

***Master-slave replication:*** In this type of replication, one server is designated as the master and all writes are made to it. The master then replicates the data to one or more slave servers, which can be used for read-only operations.

***Multi-master replication:*** In this type of replication, multiple servers can accept write operations and all servers are kept in sync. This provides higher availability and scalability but requires more complex conflict resolution and data consistency algorithms.

***Sharding:*** In this type of replication, the data is split into smaller, manageable chunks called shards, which are distributed across multiple servers. This type of replication is used to horizontally scale a database by distributing the load across multiple servers.

***Log-based replication:*** In this type of replication, the data changes are recorded in a log, and the changes are then applied to the replica. This type of replication is more efficient than other types of replication, and it can also be used for replication between different types of databases.

***Asynchronous replication:*** In this type of replication, the replica may lag behind the master, and the changes made to the master may not be immediately visible on the replica.

***Synchronous replication:*** In this type of replication, the replica is always up-to-date with the master, and changes made to the master are immediately visible on the replica. This type of replication provides higher data consistency but may have higher latency and lower availability than asynchronous replication.

Replication is a critical aspect of most database systems and it is used to ensure the data availability, scalability and fault-tolerance, to improve the performance and to keep multiple copies of the data in different locations.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>


## Q. ***What is Sharding?***
Sharding is a method of horizontally partitioning a large database into smaller, more manageable chunks called shards. Each shard is a separate, independent piece of the database that can be stored on a different server or a group of servers. The goal of sharding is to distribute the load of a database across multiple servers, so that the system can scale horizontally to handle a large amount of data and a high number of concurrent users.

Sharding is typically used in NoSQL databases, but it can also be used in relational databases. In a sharded system, the data is partitioned based on a shard key, which is a unique value that determines which shard a piece of data belongs to. The shard key can be based on a specific attribute of the data, such as a user ID or a timestamp.

Sharding has several benefits:

***1.Scale-out:*** Sharding allows a database to scale horizontally by adding more servers to the cluster. This means that as the amount of data and the number of users grow, the system can handle the increased load by adding more servers.

***2.Performance:*** By distributing the load across multiple servers, sharding can improve the performance of a database by reducing the load on any single server.

***3.High availability:*** By distributing the data across multiple servers, sharding can increase the availability of a database by reducing the impact of a single server failure.

***4.Better data distribution:*** Sharding can improve data distribution by storing data in a more optimal way.

However, sharding also introduces some additional complexity to the system, such as the need to write sharding-aware application code and the need to handle data replication and consistency across the shards.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Explain dynamodb indexing.***

Amazon DynamoDB is a NoSQL database service provided by Amazon Web Services (AWS). One of the key features of DynamoDB is its ability to create indexes on the table data, which allows for more flexible and efficient querying of the data.

In DynamoDB, an index is a data structure that contains a subset of the table data and is optimized for a specific query use case. There are two types of indexes in DynamoDB:

***1. Local Secondary Index (LSI):*** An LSI is an index that is based on the same partition key as the table, but has a different sort key. It allows for more efficient querying of the data based on the sort key.

***2. Global Secondary Index (GSI):*** A GSI is an index that has a different partition key than the table and can have a different sort key. It allows for more efficient querying of the data based on the partition key and sort key of the index.

When you create an index, you specify the attributes (columns) that you want to index, and DynamoDB automatically maintains the index as you update the table.

When you perform a query on a table, DynamoDB compares the query to the indexes on the table and uses the most efficient index to return the results. If there is no suitable index, DynamoDB performs a full table scan, which can be slower and more expensive.

It's worth mentioning that indexes do come with a cost, as each index will use additional storage, and updates to the table will require updates to the indexes as well.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>