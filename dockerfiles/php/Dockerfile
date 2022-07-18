FROM php:8.1-fpm

MAINTAINER dnikolaenko2908@gmail.com

RUN apt-get update && apt-get install -y \
	curl \
    wget \
    git \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
	libpng-dev \
	libonig-dev \
	libzip-dev \
	libmcrypt-dev \
	libldap \
	&& docker-php-ext-install -j$(nproc) iconv mbstring mysqli pdo_mysql zip

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | sudo -E bash

RUN apt install symfony-cli

WORKDIR /var/www

ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini

RUN symfony new daily-news-bot --version="6.0.*"

CMD ["php-fpm"]