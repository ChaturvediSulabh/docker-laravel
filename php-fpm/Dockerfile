FROM debian:jessie

MAINTAINER Julien Bonvarlet <jbonva@gmail.com>

RUN apt-get update && apt-get install -y php5-cli php5-fpm php5-mcrypt php5-mysql

ADD laravel.ini /etc/php5/fpm/conf.d/
ADD laravel.ini /etc/php5/cli/conf.d/

ADD laravel.pool.conf /etc/php5/fpm/pool.d/

RUN usermod -u 1000 www-data

CMD ["php5-fpm", "-F"]

EXPOSE 9000
