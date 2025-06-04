FROM php:8.1-fpm

# Install dependencies, nginx, zip, unzip, git
RUN apt-get update && apt-get install -y \
    libzip-dev zip unzip git curl \
    && docker-php-ext-install pdo pdo_mysql zip

WORKDIR /var/www/html

COPY ./yii2-app/ /var/www/html/

RUN chown -R www-data:www-data /var/www/html/runtime /var/www/html/web/assets \
    && chmod -R 775 /var/www/html/runtime /var/www/html/web/assets \
    && chown -R www-data:www-data /var/www/html

EXPOSE 8080
CMD ["php", "yii", "serve", "0.0.0.0:8080", "--docroot=web"]

