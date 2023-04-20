This tutorial will teach you how to provision a secret administration password to MongoDB.

### Prerequisite
You should have a working environment that has MongoDB installed.

You can install a MongoDB instance by clicking on the commands:
```bash
sudo apt update
sudo apt install -y mongodb
```{{exec}}

### What is MongoDB
[MongoDB](https://www.mongodb.com/) is a popular open-source NoSQL (not only SQL) document-oriented database that provides high performance, scalability, and flexibility. It was developed by MongoDB Inc. and first released in 2009.

Unlike traditional relational databases, which store data in tables with predefined schemas, MongoDB stores data in flexible JSON-like documents with dynamic schemas. This allows for greater flexibility in data modeling and makes it easier to handle unstructured data.

MongoDB also supports various features such as replication, sharding, and indexing for achieving high availability, horizontal scaling, and fast querying. It provides a rich query language with support for various query types, including ad-hoc queries, aggregation, and geospatial queries.

MongoDB is widely used by organizations of all sizes, ranging from small startups to large enterprises, in a variety of industries such as finance, healthcare, and e-commerce. It is available as both a free, open-source community edition and a paid enterprise edition with additional features and support.

### Why do we need secret administration password
A secret administration password is necessary for securing and controlling access to the administrative functions of a database, such as MongoDB. Without a strong and secure administrative password, anyone with access to the database could potentially make unauthorized changes, delete data, or perform other actions that could compromise the security and integrity of the database.

In the case of MongoDB, the administrative user has the highest level of privilege and can perform actions that regular users cannot. This includes creating and deleting databases and collections, managing users and their permissions, configuring security settings, and performing other administrative tasks.

By setting a secret administration password, you can ensure that only authorized personnel with the correct credentials can access and perform administrative functions on the database. This helps to prevent unauthorized access, data breaches, and other security incidents that could have serious consequences for the organization.
