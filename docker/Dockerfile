# Use official PHP image with Apache
FROM php:8.1-apache

# Enable Apache mod_rewrite
RUN a2enmod rewrite

# Install necessary PHP extensions
RUN apt-get update && apt-get install -y \
    libzip-dev zip unzip git \
    && docker-php-ext-install pdo pdo_mysql zip

# Set working directory
WORKDIR /var/www/html

# Copy Yii2 app files into container
COPY ./yii-app/. .

# Set file permissions
RUN chown -R www-data:www-data /var/www/html

# Expose port
EXPOSE 8080
