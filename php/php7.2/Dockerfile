FROM php:7.2-fpm

RUN apt-get update && apt-get -y install git unzip zlib1g-dev wget vim

RUN docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli && docker-php-ext-install zip bcmath


# RUN  php -r "copy('https://install.phpcomposer.com/installer', 'composer-setup. .php');" \
#     && php composer-setup.php \
#     &&  php -r "unlink('composer-setup.php');" \
#     && mv composer.phar /usr/local/bin/composer

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd




RUN pecl install redis-5.1.1 \
    && pecl install xdebug-2.8.1 \
    && docker-php-ext-enable redis xdebug

