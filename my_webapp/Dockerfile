FROM apache:latest

RUN apt-get update
RUN apt-get install -y wget vim git zip unzip zlib1g-dev libzip-dev libpng-dev
RUN docker-php-ext-install -j$(nproc) mysqli pdo_mysql gd zip pcntl exif


COPY . /var/www/html

ENV DB_PASSWORD=kinddevil