FROM php:7.4-fpm-alpine

# Install packages
RUN apk add --update \
        libzip-dev \
        icu-dev \
        openssl \
        acl \
        curl \
        unzip \
        zip \
        libpng-dev \
        libzip-dev \
        inkscape

# Install PHP extensions
RUN docker-php-ext-configure intl

RUN docker-php-ext-install -j$(nproc) \
    intl \
    pdo \
    zip \
    gd \
    pdo_mysql \
    opcache \
    mysqli \
    zip

#APCU
RUN apk add --update --no-cache --virtual .build-dependencies $PHPIZE_DEPS \
        && pecl install apcu \
        && docker-php-ext-enable apcu \
        && pecl clear-cache \
        && apk del .build-dependencies

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    ln -s $(composer config --global home) /root/composer

RUN echo "memory_limit = 2512M" >> /usr/local/etc/php/php.ini

RUN rm -rf /tmp/* /var/cache/apk/*
ENV PATH=$PATH:/root/composer/vendor/bin COMPOSER_ALLOW_SUPERUSER=1
WORKDIR /var/www/app
EXPOSE 9000