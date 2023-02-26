FROM php:8.2-fpm-alpine3.16 as build
RUN apk add --no-cache msmtp perl wget procps shadow libzip libpng libjpeg-turbo libwebp freetype icu \
supervisor

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions gd pdo_mysql pdo_pgsql intl \
    opcache exif sockets zip mysqli pcntl event redis

RUN install-php-extensions @composer

FROM build as stage
COPY conf.d/php.ini /usr/local/etc/php/conf.d/php.ini
COPY conf.d/fpm.conf /usr/local/etc/php-fpm.d/www.conf

RUN \
  mkdir /var/www/project && chown www-data: /var/www/project && \
  mkdir /var/www/log/ && touch /var/www/log/php-error.log && \
  touch /var/www/log/fpm-access.log && \
  chown www-data: /var/www/log/

RUN addgroup -g 1000 node \
    && adduser -u 1000 -G node -s /bin/sh -D node

ARG UID=1000
ARG GID=1000
ENV UID=${UID}
ENV GID=${GID}
RUN usermod -u $UID node \
  && groupmod -g $GID node

USER node

WORKDIR /var/www/project
