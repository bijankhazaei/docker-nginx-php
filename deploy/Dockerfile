ARG ALPINE_VERSION=3.17
FROM alpine:${ALPINE_VERSION}
LABEL Maintainer="Bijan KHazaei bijankhazaei@gmail.com"
LABEL Description=" Base Image for Run Laravel and some node js projects"

WORKDIR /var/www/html

RUN apk add --no-cache \
  curl \
  nginx \
  php81 \
  php81-ctype \
  php81-curl \
  php81-dom \
  php81-fpm \
  php81-gd \
  php81-intl \
  php81-mbstring \
  php81-mysqli \
  php81-opcache \
  php81-openssl \
  php81-phar \
  php81-session \
  php81-xml \
  php81-xmlreader \
  npm \
  supervisor

# Copy Configuration file for nginx
COPY config/nginx.conf /etc/nginx/nginx.conf

# Copy configuration file for - default server
COPY config/conf.d /etc/nginx/conf.d

# Copy configuration for PHP-FPM
COPY config/fpm-pool.conf /etc/php-fpm.d/www.conf
COPY config/php.ini /etc/php81/conf.d/custom.ini

# Copy configuration for supervisor
COPY config/supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# accessable file or folder for nobbody user
RUN chown -R nobody.nobody /var/www/html/ /run /var/www/lib/nginx /var/log/nginx

# Switch to nobody.
USER nobody

# Add
