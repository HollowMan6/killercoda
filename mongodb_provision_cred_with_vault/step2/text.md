You should have already setup the MongoDB access control before this step.

### Starting the Dev Server
Start a Vault server in development mode (dev server). The dev server is a built-in, pre-configured server that is not very secure but useful for playing with Vault locally. You can check [Deploy Vault tutorial](https://developer.hashicorp.com/vault/tutorials/getting-started/getting-started-deploy), for configuring and starting a non-dev server.

```bash
vault server -dev
```{{exec}}

### Set environment variables
_**Note: You need to launch a new terminal session by click on the `+` sign next to `Tab 1`.**_

Then execute the following commands:
```bash
export VAULT_ADDR='http://127.0.0.1:8200'
export VAULT_TOKEN="$(cat ~/.vault-token)"
```{{exec}}

### Verify the Server is Running
Verify the server is running by running the `vault status`{{exec}} command. If it ran successfully, the output should look like the following:

```bash
Key             Value
---             -----
Seal Type       shamir
Initialized     true
Sealed          false
Total Shares    1
Threshold       1
Version         1.13.1
Build Date      2023-03-23T12:51:35Z
Storage Type    inmem
Cluster Name    vault-cluster-141bcf10
Cluster ID      df9845ca-a0c1-d2b0-3eb7-45a845adfaee
HA Enabled      false
```

If the output looks completely different, restart the dev server and try again.

Congratulations! You've started your first Vault server.

### Setup Database Secrets Engine for MongoDB
#### 1. Enable the database secrets engine
```bash
vault secrets enable database
```{{exec}}

#### 2. Configure Vault with the proper plugin and connection information
```bash
vault write database/config/my-mongodb-database \
    plugin_name=mongodb-database-plugin \
    allowed_roles="my-role" \
    connection_url="mongodb://{{username}}:{{password}}@127.0.0.1:27017/admin" \
    username="vaultuser" \
    password="your_password_here"
```{{exec}}

#### 3. Configure a role that maps a name in Vault to a MongoDB command that executes and creates the database credential
```bash
vault write database/roles/my-role \
    db_name=my-mongodb-database \
    creation_statements='{ "db": "admin", "roles": [{ "role": "readWrite" }] }' \
    default_ttl="1h" \
    max_ttl="24h"
```{{exec}}

If all of the above steps output with `Success! ...`, congratulations! You now finished Database Secrets Engine setup for MongoDB.
