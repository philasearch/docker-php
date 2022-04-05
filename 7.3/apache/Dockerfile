FROM php:7.3.33-apache

RUN a2enmod rewrite
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libtidy-dev \
        git \
        vim \
        libzip-dev \
        libsodium-dev \
        libcurl4-openssl-dev \
        libxml2-dev \
    && pecl install mcrypt-1.0.2 sodium \ \
    && docker-php-ext-enable mcrypt \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-configure curl --with-curl \
    && docker-php-ext-install -j$(nproc) gd pdo pdo_mysql tidy mbstring bcmath json mysqli zip curl pcntl xml dom \
    && pear install Mail_Mime Mail Net_SMTP \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
