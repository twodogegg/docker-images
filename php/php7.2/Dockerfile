FROM php:7.2-fpm

RUN docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli && docker-php-ext-install zip

RUN apt-get update && apt-get -y install git unzip

RUN  php -r "readfile('https://getcomposer.org/installer');" | php && mv composer.phar /usr/local/bin/compose && 