FROM php:7-fpm

# Install dependencies
RUN apt-get update && apt-get install --no-install-recommends -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libcurl4-gnutls-dev libmcrypt-dev libpq-dev
# RUN apt-get update && apt-get install --no-install-recommends -y zlib1g-dev libicu-dev g++ unixodbc-dev libxml2-dev libaio-dev freetds-dev libssl-dev openssl

# Configure the gd library
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

# Install required PHP extensions
RUN docker-php-ext-install curl gd mbstring mcrypt pdo pdo_mysql pdo_pgsql json zip