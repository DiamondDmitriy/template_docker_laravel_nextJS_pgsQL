FROM php:8.0

RUN apt-get update -y && apt-get install -y libonig-dev curl openssl zip unzip git
# RUN curl -sS https:getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- \
        --filename=composer \
        --install-dir=/usr/local/bin && \
        echo "alias composer='composer'" >> /root/.bashrc && \
        composer

RUN docker-php-ext-install pdo mbstring pdo_mysql 

WORKDIR /app/backend
COPY . .
RUN composer install --prefer-source --no-interaction

EXPOSE 8000
CMD php artisan serve --host=0.0.0.0