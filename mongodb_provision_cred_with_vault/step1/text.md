You should have already setup a MongoDB instance and installed HashiCorp Vault before this step.

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

### Create the administrative user

Create a new administrative user for HashiCorp Vault by running the following command:

```bash
db.createUser({
  user: "vaultuser",
  pwd: "your_password_here",
  roles: [ { role: "root", db: "admin" } ]
})
```{{exec}}

This will create a new administrative user with the username `vaultuser` and the password `your_password_here`. You can replace `your_password_here` with a strong password of your choice. The command should respond with `Successfully added user ...`.

### Exit the MongoDB shell
Once you have created the administrative user, exit the MongoDB shell by running the following command:

```bash
exit
```{{exec}}

### Restart MongoDB with authentication enabled
To enable authentication, you need to set `auth = true` in `/etc/mongodb.conf`
```bash
cat /etc/mongodb.conf | grep auth
sudo tee -a /etc/mongodb.conf <<< "auth = true"
cat /etc/mongodb.conf | grep auth
```{{exec}}

Now you can restart MongoDB. The exact steps for doing this will depend on your operating system and how you installed MongoDB. For example, on killercoda here (the Linux systems uses systemd), you can use the following command:

```bash
sudo systemctl restart mongodb
```{{exec}}
