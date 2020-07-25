FROM php:7.3-fpm

WORKDIR /var/www/html

RUN apt-get update && apt-get -y install git unzip zlib1g-dev wget vim

RUN docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli && docker-php-ext-install bcmath



RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd




RUN pecl install redis \
    && pecl install xdebug \
    && docker-php-ext-enable redis xdebug

RUN echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini

COPY ./sg11/ .

RUN echo "extension=/root/sg11/ixed.7.3.lin" >> /usr/local/etc/php/conf.d/sg11.ini

COPY ./sg11/ixed.7.3.lin ./sg11/ixed.7.3.lin


RUN  php -r "copy('https://install.phpcomposer.com/installer', 'composer-setup.php');" \
    && php composer-setup.php \
    &&  php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

RUN apt-get update && apt-get -y libzip-dev \
    && docker-php-ext-install zip