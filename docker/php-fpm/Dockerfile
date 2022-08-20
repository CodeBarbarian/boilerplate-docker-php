FROM php:8.1.10RC1-fpm-alpine3.16

# Add extensions to php first
RUN docker-php-ext-install pdo_mysql



# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www

COPY "composer.json" .
COPY "composer.lock" .

# Something something
RUN composer dump-autoload --optimize
RUN composer update

# default command when the container is built and ready to go, next to last command
CMD ["php-fpm"]

# Last command, need to expose the port
EXPOSE 9000