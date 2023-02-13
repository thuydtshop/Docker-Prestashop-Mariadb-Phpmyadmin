# Try to change the php version for compatibility with your Prestashop version
FROM php:8.2-apache

RUN a2enmod rewrite headers

RUN apt-get update && \
    apt-get install -y --no-install-recommends git zip libzip-dev

# Install opcache extension for PHP accelerator
# RUN docker-php-ext-install opcache \
#     && docker-php-ext-enable opcache \
#     && rm -rf /var/lib/apt/lists/* \
#     && apt-get autoremove -y

RUN set -xe \
    && apt update \
    && apt install -y libpng-dev libjpeg-dev libwebp-dev unzip libicu-dev \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-configure gd --with-jpeg=/usr --with-webp=/usr \
    && docker-php-ext-install gd mysqli pdo_mysql zip intl \
    && chown -R www-data:www-data /var/www/html


