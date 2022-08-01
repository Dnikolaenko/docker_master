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
	&& docker-php-ext-install -j$(nproc) iconv mbstring mysqli pdo_mysql zip

COPY --from=composer /usr/bin/composer /usr/bin/composer

WORKDIR /var/www

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"

CMD composer i -o ; php-fpm