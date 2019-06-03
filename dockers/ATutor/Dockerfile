FROM alpine:3.3

RUN apk update


RUN apk add php-apache2
RUN apk add mysql

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

WORKDIR /var/www/localhost/htdocs
RUN mkdir -p /run/apache2

COPY ATutor-2.2.1.tar.gz /tmp/
RUN tar xzf /tmp/ATutor-2.2.1.tar.gz
COPY index.html .

RUN apk add php-zlib
RUN apk add php-mysql
RUN apk add curl

RUN mysql_install_db --user=root
RUN mkdir /run/mysqld

RUN apk add bash

ENTRYPOINT [ "bash", "-c", "(mysqld --user=root &) && /usr/sbin/httpd -D FOREGROUND"] 