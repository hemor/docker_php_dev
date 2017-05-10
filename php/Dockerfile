FROM php:7-fpm

# Install dependencies
RUN apt-get update && apt-get install --no-install-recommends -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libcurl4-gnutls-dev libmcrypt-dev libpq-dev
# RUN apt-get update && apt-get install --no-install-recommends -y zlib1g-dev libicu-dev g++ unixodbc-dev libxml2-dev libaio-dev freetds-dev libssl-dev openssl

# Configure the gd library
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

# Install required PHP extensions
RUN docker-php-ext-install curl gd mbstring mcrypt pdo pdo_mysql pdo_pgsql json zip

# Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('SHA384', 'composer-setup.php') === '669656bab3166a7aff8a7506b8cb2d1c292f042046c5a994c43155c0be6190fa0355160742ab2e1c88d40d5be660b410') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php --install-dir=/usr/local/bin --filename=composer
RUN php -r "unlink('composer-setup.php');"