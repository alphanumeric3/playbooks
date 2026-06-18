# Forgejo

Variables:
- `name`: Name of the instance
- `slogan`: Slogan shown on homepage, page titles, etc

# Creating an initial user

After installing, create the admin user on the host:

```sh
sudo -u git forgejo \
	--config /etc/forgejo/app.ini \
	admin user create --admin \
	 --username admin \
	 --email user@noreply.localhost \
	 --random-password \
	 --must-change-password
```
