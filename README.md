docker-laravel
==============

Just a litle Docker POC in order to have a complete stack for running Laravel into Docker containers using docker-compose tool.

# Installation

First, clone this repository:

```bash
$ git clone https://github.com/tyloo/docker-laravel.git
```

Next, put your Laravel application into the `www` folder and do not forget to add `app.dev` (with your Docker host IP) in your `/etc/hosts` file.

Now, here's the magic. Simply run:

```bash
$ docker-compose up -d
```

You are done, you can visit your Laravel application in `http://app.dev`

# How it works?

* `data`: This is the Laravel application code container,
* `db`: This is the MariaDB database container (can be changed to MySQL, postgresql or whatever in `docker-compose.yml` file),
* `php`: This is the PHP-FPM container and is linked to the `db` and `nginx` container,
* `nginx`: This is the Nginx webserver container and is linked to the `data`container,

This results in the following running containers:

```bash
> $ docker-compose ps
         Name                  Command              State           Ports
    ------------------------------------------------------------------------------
    devbox_data_1    /bin/bash                      Up
    devbox_db_1      /docker-entrypoint.sh mysqld   Up      0.0.0.0:3306->3306/tcp
    devbox_nginx_1   nginx                          Up      0.0.0.0:80->80/tcp
    devbox_php_1     /usr/sbin/php5-fpm -F          Up      9000/tcp
```

# Read logs

You can access Nginx and Laravel application logs in the following directories into your host machine:

* `logs/nginx`
* `logs/laravel`
