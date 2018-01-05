FROM php:7.1-apache

RUN apt-get update && \
    apt-get install -y \
        zlib1g-dev

RUN apt-get update -y && apt-get install -y libpng-dev  

RUN docker-php-ext-install gd

RUN docker-php-ext-enable opcache

RUN docker-php-ext-install pdo pdo_mysql

COPY 000-default.conf /etc/apache2/sites-enabled/

RUN a2enmod rewrite

RUN service apache2 restart