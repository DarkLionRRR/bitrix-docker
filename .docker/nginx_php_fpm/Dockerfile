FROM php:8.3-fpm

RUN apt-get update && apt-get install -y nginx \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev

RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-install gd opcache pdo pdo_mysql mysqli

COPY ./.docker/nginx_php_fpm/nginx/sites-enabled /etc/nginx/sites-enabled

COPY ./.docker/nginx_php_fpm/php /usr/local/etc/php-fpm.d

EXPOSE 80

CMD service nginx start && php-fpm