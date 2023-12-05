FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
      apt-utils \
      libpq-dev \
      libpng-dev \
      libjpeg-dev \
      libwebp-dev \
      libzip-dev \
      zip unzip \
      libfreetype6-dev \
      libjpeg62-turbo-dev \
      webp \
      jpegoptim \
      optipng \
      curl \
      sendmail \
      nodejs npm \
      git && \
      pecl install xdebug-3.1.6 && \
      docker-php-ext-enable xdebug && \
      docker-php-ext-install opcache && \
      docker-php-ext-install mysqli && \
      docker-php-ext-install pdo_mysql && \
      docker-php-ext-install bcmath && \
      docker-php-ext-install gd && \
      docker-php-ext-install zip && \
      docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp && \
      docker-php-ext-install -j$(nproc) gd && \
      apt-get clean && \
      rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY ./_docker/config/php/conf.d/php.ini /usr/local/etc/php/conf.d/php.ini
COPY ./_docker/config/php/conf.d/sendmail.ini /usr/local/etc/php/conf.d/sendmail.ini
COPY ./_docker/config/php/conf.d/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

# composer
ENV COMPOSER_ALLOW_SUPERUSER=1
RUN curl -sS https://getcomposer.org/installer | php -- \
    --filename=composer \
    --install-dir=/usr/local/bin

WORKDIR /var/www