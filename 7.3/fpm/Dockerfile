FROM php:7.3.4-apache

RUN a2enmod rewrite
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libssl-dev \
        libicu-dev \
        libtidy-dev \
        libpq-dev \
        libmcrypt-dev \
        git \
        libzip-dev \
        libsodium-dev \
    && pecl install mcrypt-1.0.2 sodium \
    && docker-php-ext-enable mcrypt \
    && docker-php-ext-install -j$(nproc) \
        iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) \
        gd \
        pdo pdo_mysql \
        tidy \
        mbstring \
        bcmath \
        json \
        mysqli \
        zip \
        intl \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
