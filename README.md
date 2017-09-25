# fsnd_p6_server

## Access

[188.166.100.114/](http://188.166.100.114/)

## Installed

* [PostgreSQL](https://www.postgresql.org/)
* [Apache2](https://httpd.apache.org/)
* [htop](http://hisham.hm/htop/)

## Configs

### Python / WSGI

The catalog python3 app was pulled from [github](https://github.com/arccoza/fsnd_p4_catalog) into `/etc/www/fsnd_p4_catalog`. The `app.wsgi` file was later created for Apache and pulled.

### Apache

An Apache virtual server was configured pointing to `/etc/www/fsnd_p4_catalog`, and enabled. The default site was disabled.

### PostgreSQL

A Postgres role was added for the catalog app to use for DB access, using peer auth.

## References

[http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/](http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/)

[https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets)

[https://askubuntu.com/a/524362](https://askubuntu.com/a/524362)
