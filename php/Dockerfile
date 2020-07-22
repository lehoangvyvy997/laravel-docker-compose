# Dockerfile
FROM php:7.2-fpm

RUN apt-get update \
   && apt-get install -y git \
   && apt-get install -y curl \
   && apt-get install -y vim

# RUN apt-get install -y -q --no-install-recommends \
#         apt-transport-https \
#         ca-certificates \
#         libssl-dev \
#         python \
#         autoconf \
#         ssl-cert \
#     && apt-get install -y node-gyp \
#     && apt-get clean \
#     && rm -rf /var/lib/apt/lists/*

# # install node
# USER root
# RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - \
#     && apt-get install -y nodejs \
#     && curl -L https://www.npmjs.com/install.sh | sh
# # confirm installation
# RUN node -v
# RUN npm -v

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer
 
USER root
RUN apt-get install -y default-mysql-client
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN apt-get install -y sendmail libpng-dev libicu-dev
RUN docker-php-ext-configure intl
RUN docker-php-ext-install mbstring gd intl

RUN apt-get install -y p7zip \
    p7zip-full \
    unace \
    zip \
    unzip \
    file-roller \
    && rm -rf /var/lib/apt/lists/*
   
COPY ./config/laravel.ini /usr/local/etc/php/conf.d

WORKDIR /var/www/html
EXPOSE 9000 