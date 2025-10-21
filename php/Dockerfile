FROM php:8.4.13-fpm@sha256:231ab3ac3db542e1d019a35abee1bd106d278a5712d1dc2bb4fbe103de016792

ENV IPE_GD_WITHOUTAVIF=1

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    libzip-dev zip \
    libbz2-dev libxml2-dev libxslt-dev \
    libwebp-dev libjpeg62-turbo-dev libpng-dev libxpm-dev libfreetype6-dev \
    gettext wget unzip libicu-dev libkrb5-dev \
 && docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg --with-webp \
 && docker-php-ext-install \
      bcmath \
      gd \
      intl \
      mysqli \
      pdo_mysql \
      sockets \
      bz2 \
      soap \
      zip \
      ftp \
 && rm -rf /var/lib/apt/lists/*

RUN usermod -u 1000 www-data && groupmod -g 1000 www-data

USER www-data

COPY --link --from=composer/composer:2-bin /composer /usr/local/bin/composer