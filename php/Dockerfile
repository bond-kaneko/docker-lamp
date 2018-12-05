FROM php:7.2.4-apache

RUN apt-get update && \
    apt-get install -y libpq-dev libxml2 libxml2-dev libicu-dev git ssl-cert rsyslog cron vim git gnupg
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install pdo_mysql mbstring xml pdo intl opcache zip

RUN usermod -u 1000 www-data && groupmod -g 1000 www-data
RUN a2enmod rewrite

EXPOSE 80

