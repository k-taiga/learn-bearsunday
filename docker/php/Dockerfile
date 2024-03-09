FROM php:8.1.9-apache-buster
SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]

RUN apt-get update && \
  apt-get -y install git unzip libzip-dev libicu-dev zlib1g-dev sqlite3 libsqlite3-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  docker-php-ext-install pdo_sqlite && \
  docker-php-ext-enable pdo_sqlite && \
  docker-php-ext-install opcache && \
  pecl install apcu && \
  echo "extension=apcu.so" > $PHP_INI_DIR/conf.d/apcu.ini

COPY --from=composer /usr/bin/composer /usr/bin/composer

WORKDIR /work