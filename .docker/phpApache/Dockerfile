ARG PHP_VERSION=""
FROM php:${PHP_VERSION}-apache

RUN apt-get update \
    && apt-get install -y --no-install-recommends git zlib1g-dev libzip-dev zip unzip mysql-client

RUN docker-php-ext-install pdo_mysql zip mysqli
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

RUN curl -sSk https://getcomposer.org/installer | php -- --disable-tls && \
       mv composer.phar /usr/local/bin/composer

RUN groupadd dev -g 999
RUN useradd dev -g dev -d /var/www -m
RUN chown -R dev:dev /var/www

RUN rm -rf /var/lib/apt/lists/*
RUN a2enmod rewrite