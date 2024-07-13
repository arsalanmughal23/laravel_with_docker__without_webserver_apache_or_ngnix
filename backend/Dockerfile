FROM php:8.2

# RUN apt-get update -y && apt-get install -y openssl zip unzip git
RUN apt-get update -y && apt-get install -y openssl zip unzip git libonig-dev libzip-dev libpng-dev libjpeg-dev libfreetype6-dev
RUN docker-php-ext-configure gd --with-freetype --with-jpeg

# RUN docker-php-ext-install pdo mbstring pdo_mysql
RUN docker-php-ext-install pdo pdo_mysql mbstring zip gd

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /app/backend
COPY . .
RUN composer install

EXPOSE 8000
CMD php artisan serve --host=0.0.0.0