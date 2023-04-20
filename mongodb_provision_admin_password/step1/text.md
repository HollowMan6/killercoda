You should have already setup a MongoDB instance before this step.

### Connect to the MongoDB instance

You can use the MongoDB shell to connect to your instance:

```bash
mongo
```{{exec}}

You can see the following warning when you enter their shell. Now you know you haven't provisioned a secret admin password.

```text
WARNING: Access control is not enabled for the database.
         Read and write access to data and configuration is unrestricted.
```

### Switch to the admin database

Once you are connected to the MongoDB shell, switch to the admin database:

```bash
use admin
```{{exec}}

Now you can create any collection you want at any database (as the following command is successful with respond `{ "ok" : 1 }`), which should be restricted since you are not authenticated to the database.

```bash
db.createCollection("test1")
```{{exec}}

### Create the administrative user

Create a new administrative user by running the following command:

```bash
db.createUser({
  user: "admin",
  pwd: "your_password_here",
  roles: [ { role: "root", db: "admin" } ]
})
```{{exec}}

This will create a new administrative user with the username `admin` and the password `your_password_here`. You can replace `your_password_here` with a strong password of your choice. The command should respond with `Successfully added user ...`.

### Exit the MongoDB shell
Once you have created the administrative user, exit the MongoDB shell by running the following command:

```bash
exit
```{{exec}}
