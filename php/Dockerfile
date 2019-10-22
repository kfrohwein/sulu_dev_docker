FROM php:7.2-fpm-alpine

ARG USER_ID

RUN apk --no-cache update \
        && apk --no-cache upgrade \
        && apk add --no-cache --virtual build-dependencies \
        libpng-dev \
        zlib-dev \
        curl-dev \
        icu-dev \
        build-base \
        imagemagick-dev \
        autoconf \
        && apk add --no-cache \
        icu-libs \
        imagemagick \
        postgresql-dev \
        composer

RUN docker-php-ext-install zip \
    && docker-php-ext-install pdo_pgsql \
    && docker-php-ext-install opcache

RUN docker-php-ext-configure intl \
    && docker-php-ext-install intl

RUN pecl install \
    imagick \
    && docker-php-ext-enable \
    imagick \
    && apk del build-dependencies

RUN if [ ! -z ${USER_ID} ]; then addgroup -g ${USER_ID} sulu; fi \
    && if [ ! -z ${USER_ID} ]; then adduser -u ${USER_ID} -H -h /home/sulu -G sulu -s /sbin/nologin -D sulu; fi


USER sulu
WORKDIR /var/www/project
