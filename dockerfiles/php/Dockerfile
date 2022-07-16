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

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www

ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini

CMD ["php-fpm"]