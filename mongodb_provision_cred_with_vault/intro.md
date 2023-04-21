This tutorial will teach you how to provision MongoDB credentials using HashiCorp Vault.

### Prerequisite
You should have a working environment that has the following software installed:
- [MongoDB](https://www.mongodb.com/docs/manual/installation/)
- [HashiCorp Vault](https://developer.hashicorp.com/vault/docs/install)

You can setup the environment in killercoda by clicking on the commands.

#### 1. Setup HashiCorp Vault installation repository
```bash
sudo apt update
sudo apt install -y gpg
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
gpg --no-default-keyring --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg --fingerprint
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
```{{exec}}

#### 2. Install the MongoDB instance and HashiCorp Vault
```bash
sudo apt update
sudo apt install -y mongodb vault
```{{exec}}

Then start this tutorial by scrolling down to the bottom and click `START`.

### What is MongoDB
[MongoDB](https://www.mongodb.com/) is a popular open-source NoSQL (not only SQL) document-oriented database that provides high performance, scalability, and flexibility. It was developed by MongoDB Inc. and first released in 2009.

Unlike traditional relational databases, which store data in tables with predefined schemas, MongoDB stores data in flexible JSON-like documents with dynamic schemas. This allows for greater flexibility in data modeling and makes it easier to handle unstructured data.

MongoDB also supports various features such as replication, sharding, and indexing for achieving high availability, horizontal scaling, and fast querying. It provides a rich query language with support for various query types, including ad-hoc queries, aggregation, and geospatial queries.

MongoDB is widely used by organizations of all sizes, ranging from small startups to large enterprises, in a variety of industries such as finance, healthcare, and e-commerce. It is available as both a free, open-source community edition and a paid enterprise edition with additional features and support.

### Why do we need HashiCorp Vault Secrets Engines for Databases
[HashiCorp Vault](https://www.vaultproject.io/) Secrets Engines for Databases provide a secure way to manage and protect sensitive data such as database credentials, API keys, and other secrets. Here are some reasons why you might need a HashiCorp Vault Secrets Engine for your database:
#### 1. Centralized Secrets Management
A centralized secrets management solution like HashiCorp Vault helps to consolidate secrets across your infrastructure, including databases. This means that you can store all of your database credentials in one place, making it easier to manage and secure them.
#### 2. Granular Access Control
With Vault Secrets Engines, you can define policies that restrict access to specific databases or database objects based on user or application permissions. This provides a finer level of control over access to sensitive data, helping to reduce the risk of unauthorized access or data breaches.
#### 3. Automated Secrets Rotation
Vault Secrets Engines provide the ability to automatically rotate database credentials, reducing the risk of credential theft or misuse. This is particularly important for databases that require frequent password changes.
#### 4. Audit Trail
Vault Secrets Engines provide an audit trail of all access and changes to secrets. This helps with compliance requirements and provides visibility into who is accessing what data.
#### 5. Integration with Other Vault Features
Vault Secrets Engines integrate with other Vault features such as dynamic secrets, which allows Vault to generate credentials on-demand for specific use cases. This provides an added layer of security, as the credentials are only available for the duration of the request, reducing the risk of credential theft or misuse.
