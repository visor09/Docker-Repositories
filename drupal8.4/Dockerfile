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

RUN apt-get install -y git

WORKDIR /var/www/html

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"

# RUN pwd

# RUN ls -lt

RUN mv composer.phar /usr/bin/composer