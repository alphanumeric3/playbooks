# Forgejo

No extra variables at the moment.

# Creating an initial user

After installing, create the admin user on the host:

```sh
sudo -u git forgejo \
	--config /etc/forgejo/app.ini \
	admin user create --admin \
	 --username plate \
	 --email user@noreply.localhost \
	 --random-password \
	 --must-change-password
```
