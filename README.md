# Docker Project Demo

## django-mysqlclient

`python:3.7-alpine` is used as the base to minimize the file size to ~100MB.

The compose file includes three services:

- nginx: as reverse proxy and static file web server
- python: wsgi app
- db: mysql database

The src folder is not provided for simplicity. Use the following commands to initialize a Django project.

```bash
cd django-mysqlclient
docker-compose run python django-admin.py startproject app .
docker-compose run python ./manage.py migrate
docker-compose run python ./manage.py createsuperuser
docker-compose run python ./manage.py collectstatic
docker-compose up -d
```

## Reference

- https://medium.com/@kenkono/docker-for-django-nginx-and-mysql-5960a611829e
- https://www.ukeyslabo.com/development/docker/python-alpine-django-mysql-err/
