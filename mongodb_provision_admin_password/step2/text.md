You should have already setup the admin password before this step.

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
