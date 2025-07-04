FROM php:8.4.10-fpm@sha256:c9d4beea5abc16ba2c5a52aa0caafd534500682bbec17411fad9198bb47ec196

ENV IPE_GD_WITHOUTAVIF=1

RUN apt-get clean \
 && apt-get update \
 && apt-get install -y libzip-dev zip \
    libbz2-dev libxml2-dev libxslt-dev \
    libwebp-dev \
    libjpeg62-turbo-dev \
    libpng-dev libxpm-dev \
    libfreetype6-dev \
    gettext \
    wget \
    unzip \
    libicu-dev libc-client-dev libkrb5-dev \
    --no-install-recommends \
&& docker-php-ext-configure gd \
       --enable-gd --with-freetype --with-jpeg \
       --with-webp \
#&& docker-php-ext-configure imap --with-kerberos --with-imap-ssl \
&& docker-php-ext-install bcmath \
      gd \
      intl \
      mysqli \
      pdo_mysql \
      sockets \
      bz2 \
      intl \
      soap \
      zip \
&& apt-get autoremove -y && apt-get clean && rm -rf /var/lib/apt/lists/*