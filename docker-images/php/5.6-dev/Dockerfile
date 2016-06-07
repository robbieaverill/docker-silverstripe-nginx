FROM php:5.6-fpm

# Install
RUN buildDeps=" \
        libpng12-dev \
        libjpeg-dev \
        libmcrypt-dev \
        libxml2-dev \
        freetype* \
    "; \
    set -x \
    && apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-configure \
    gd --with-png-dir=/usr --with-jpeg-dir=/usr --with-freetype-dir \
    && docker-php-ext-install \
    gd \
    mbstring \
    mysqli \
    mcrypt \
    mysql \
    pdo_mysql \
    soap \
    xml \
    zip \
    && apt-get update -qy && apt-get install -qy git-core \
    && apt-get purge -y --auto-remove

# Configure
COPY php.ini /usr/local/etc/php/php.ini
COPY php-fpm.conf /usr/local/etc/

# Make sure the volume mount point is empty
RUN rm -rf /var/www/*

WORKDIR /var/www
