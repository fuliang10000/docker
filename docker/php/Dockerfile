FROM php:7.1-fpm

#解压扩展目录
RUN docker-php-source extract
RUN apt-get update
RUN apt-get install -y \
    libfreetype6-dev \
    libtool \
    libjpeg62-turbo-dev \
    libpng-dev \
    libzip-dev \
    libmcrypt-dev \
    openssl \
    libssl-dev \
    libxml2
#安装扩展
RUN docker-php-ext-install -j$(nproc) iconv
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install -j$(nproc) gd
RUN docker-php-ext-install -j$(nproc) bcmath
RUN docker-php-ext-install -j$(nproc) pdo
RUN docker-php-ext-install -j$(nproc) mbstring
RUN docker-php-ext-install -j$(nproc) pdo_mysql
RUN docker-php-ext-install -j$(nproc) opcache
RUN docker-php-ext-install -j$(nproc) mysqli
RUN docker-php-ext-install -j$(nproc) zip
RUN docker-php-ext-install -j$(nproc) pcntl
RUN docker-php-ext-install -j$(nproc) tokenizer
#RUN pecl install redis-4.0.1 && docker-php-ext-enable redis
#RUN pecl install mcrypt-1.0.0 && docker-php-ext-enable mcrypt
#删除解压的扩展
RUN rm -rf /tmp/pear
RUN docker-php-source delete

RUN cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini
RUN php -v
WORKDIR /var/www/zhongdong
