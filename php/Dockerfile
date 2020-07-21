# Dockerfile
FROM php:7.2-fpm

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer

RUN apt-get update \
   && apt-get install -y git

RUN apt-get install -y vim

USER root
RUN apt-get install -y default-mysql-client
# RUN docker-php-ext-install mysqli \
#     && docker-php-ext-enable mysqli
RUN docker-php-ext-install mysqli pdo pdo_mysql

RUN apt-get install -y p7zip \
    p7zip-full \
    unace \
    zip \
    unzip \
    xz-utils \
    sharutils \
    uudeview \
    mpack \
    arj \
    cabextract \
    file-roller \
    && rm -rf /var/lib/apt/lists/*

COPY ./config/laravel.ini /usr/local/etc/php/conf.d

WORKDIR /var/www/html
EXPOSE 9000 