From php:7.2-fpm

RUN apt-get -yqq update \
    && apt-get -yqq install -yqq --no-install-recommends unzip wget libpng-dev curl libcurl4 gnupg2 locales apt-transport-https  build-essential libaio1 zlib1g-dev \
    && echo "en_US.UTF-8 UTF-8" > /etc/locale.gen \
    && locale-gen \
    && docker-php-ext-install pdo_mysql zip gd

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer global require "laravel/installer"

RUN rm -rf /var/lib/apt/lists/ && curl -sL https://deb.nodesource.com/setup_10.x | /bin/bash -
RUN apt-get install -yqq nodejs
RUN curl -L https://npmjs.org/install.sh | /bin/bash -
RUN npm install --global cross-env

RUN apt-get install -y libxml2-dev \
    && docker-php-ext-configure intl --enable-intl \
    && docker-php-ext-configure soap --enable-soap \
    && docker-php-ext-install intl \
    && docker-php-ext-install soap

WORKDIR /var/www/html

RUN chown -R www-data:www-data /var/www/html

RUN useradd -d /var/wwww/html appuser
RUN adduser appuser sudo
USER appuser