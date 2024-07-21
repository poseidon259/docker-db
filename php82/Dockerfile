FROM php:8.2-fpm

# Cài đặt các dependencies và extensions
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip

RUN docker-php-ext-install pdo pdo_mysql mbstring exif pcntl bcmath gd

# Cài đặt Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Thiết lập thư mục làm việc
WORKDIR /var/www/html

# Sao chép các file của ứng dụng
COPY . .

# Cài đặt dependencies
RUN composer install --no-scripts --no-autoloader --prefer-dist

# Tạo autoloader
RUN composer dump-autoload --optimize

# Thiết lập quyền
RUN chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache