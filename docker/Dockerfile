FROM php:8.1-fpm

RUN apt-get update && apt-get install -y libzip-dev zip unzip git \
    && docker-php-ext-install pdo pdo_mysql zip

WORKDIR /var/www/html

COPY ./yii2-app/ /var/www/html/


RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 755 /var/www/html

EXPOSE 9000

CMD ["php-fpm"]
