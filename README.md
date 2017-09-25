# fsnd_p6_server

## Access

[188.166.100.114/](http://188.166.100.114/)

## Installed

* [PostgreSQL](https://www.postgresql.org/)
* [Apache2](https://httpd.apache.org/)
* [htop](http://hisham.hm/htop/)

## Configs

### Python / WSGI

The catalog python3 app was pulled from [github](https://github.com/arccoza/fsnd_p4_catalog) into `/etc/www/fsnd_p4_catalog`. The `app.wsgi` file was later created for Apache and pulled, the same wsgi file is in this repo.

There were issues with module references when running the app through WSGI. The app does not use a virtualenv, nor global packages, but rather locally installed dependencies in the `lib` directory (installed with `pip install -r requirements.txt -t lib`). The original app imported a local module to add `lib` to the site packages path, but under WSGI this didn't work, so in `app.wsgi` additional package paths had to be added to ensure local modules would load.

There was also an issue with the CWD under WSGI, which is not the app root but rather the system root, which required a small patch to the catalog app.

### Apache

An Apache virtual server was configured pointing to `/etc/www/fsnd_p4_catalog`, and enabled. The conf file is in this repo. The default site was disabled.

### PostgreSQL

A Postgres role was added for the catalog app to use for DB access, using peer auth.

## References

1. [http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/](http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/)

2. [https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps)

3. [https://stackoverflow.com/questions/13329354/flask-mod-wsgi-and-apache-importerror](https://stackoverflow.com/questions/13329354/flask-mod-wsgi-and-apache-importerror)

4. [https://stackoverflow.com/questions/12081789/pythons-working-directory-when-running-with-wsgi-and-apache](https://stackoverflow.com/questions/12081789/pythons-working-directory-when-running-with-wsgi-and-apache)

4. [https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets)

5. [https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04)

6. [https://stackoverflow.com/questions/40537159/psycopg2-peer-authentication-for-user-postgress](https://stackoverflow.com/questions/40537159/psycopg2-peer-authentication-for-user-postgress)

7. [https://askubuntu.com/a/524362](https://askubuntu.com/a/524362)
