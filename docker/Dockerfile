FROM php:8.1-fpm

# Install dependencies, nginx, zip, unzip, git
RUN apt-get update && apt-get install -y \
    nginx \
    libzip-dev zip unzip git \
    && docker-php-ext-install pdo pdo_mysql zip \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www/html

COPY ./yii2-app/ /var/www/html/

# Copy custom nginx config
COPY ./docker/nginx.conf /etc/nginx/sites-available/default

RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 755 /var/www/html

EXPOSE 80

# Start php-fpm and nginx together using supervisord or a bash script
CMD service php8.1-fpm start && nginx -g 'daemon off;'
