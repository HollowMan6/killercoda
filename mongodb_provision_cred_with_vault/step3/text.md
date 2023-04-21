You should have already setup HashiCorp Vault Database Secrets Engine for MongoDB before this step.

### Get credentials
After the secrets engine is configured and a user has a Vault token with the proper permission, it can generate credentials:
```bash
vault read database/creds/my-role
```{{exec}}

### Connect to the MongoDB instance with generated credentials
Now you can use the generated credentials in order to perform administrative tasks.

We first get a useable credential from the command we just used above.
```bash
vault read database/creds/my-role > credential.txt
username=$(cat credential.txt | grep username | tr -s ' ' | cut -d' ' -f2)
password=$(cat credential.txt | grep password | tr -s ' ' | cut -d' ' -f2)
echo $username
echo $password
```{{exec}}

Then we can authenticate into the MongoDB database using the credential.
```bash
mongo -u "$username" -p "$password" --authenticationDatabase admin
```{{exec}}

Once you are authenticated, you can perform administrative tasks using the MongoDB shell, like creating a collection in the admin database:

```bash
use admin
db.createCollection("test2")
```{{exec}}

The command should work without any issue (respond with `{ "ok" : 1 }`).

### Verify that we need authentication

Now, let's try to perform administrative tasks without authentication. Try to create a collection again in the admin database.

```bash
exit
mongo
use admin
db.createCollection("test3")
```{{exec}}

Since we didn't authenticate outself to the database, The command should fail with the following response:

```bash
{
    "ok" : 0,
    "errmsg" : "there are no users authenticated",
    "code" : 13,
    "codeName" : "Unauthorized"
}
```
