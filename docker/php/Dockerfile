FROM php:7.2-fpm
#COPY php.ini /usr/local/etc/php/
COPY docker/php/php.ini /usr/local/etc/php/

RUN apt-get update \
  && apt-get install -y zlib1g-dev mariadb-client \
  && docker-php-ext-install zip pdo_mysql

#Composer install
COPY --from=composer /usr/bin/composer /usr/bin/composer

# 環境変数設定
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

WORKDIR /var/www/html

# Laravelインストール
RUN composer global require "laravel/installer"
# RUN laravel new tomita_project
RUN composer create-project --prefer-dist laravel/laravel tomita_project
# RUN git clone clone_url

WORKDIR /var/www/html/tomita_project
RUN chmod -R 777 bootstrap/cache
RUN chmod -R 777 storage
RUN echo "<?php phpinfo();" > public/index.php
# ポートを公開
EXPOSE 9000
