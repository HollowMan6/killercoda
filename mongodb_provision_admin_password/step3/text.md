You should have already restarted MongoDB with authentication enabled before this step.

### Connect to the MongoDB instance again
Now you need to authenticate using the administrative user you created in step 1 in order to perform administrative tasks. You can do this by running the following command:

```bash
mongo -u admin -p your_password_here --authenticationDatabase admin
```{{exec}}

Replace "your_password_here" with the password you created in step 1.

Once you are authenticated, you can perform administrative tasks using the MongoDB shell, like creating a collection in the database:

```bash
db.createCollection("test2")
```{{exec}}

The command should work without any issue (respond with `{ "ok" : 1 }`).

### Verify that we need authentication

Now, let's try to perform administrative tasks without authentication. Try to create a collection again in the database.

```bash
exit
mongo
db.createCollection("test2")
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
