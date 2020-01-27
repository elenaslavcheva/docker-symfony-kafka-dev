FROM php:7.2.13-fpm-stretch

ARG LIBRDKAFKA_VERSION=1.3.0
ARG EXT_RDKAFKA_VERSION=3.0.3

#Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && apt-get update && apt-get install -y git libzip-dev unzip vim \
    && docker-php-ext-install zip 
    
RUN git clone --depth 1 --branch v$LIBRDKAFKA_VERSION https://github.com/edenhill/librdkafka.git \
    && cd librdkafka \ 
    && ./configure \
    && make \
    && make install
    
RUN pecl channel-update pecl.php.net \
    && pecl install rdkafka-$EXT_RDKAFKA_VERSION \
    && docker-php-ext-enable rdkafka \
    && rm -rf /librdkafka    
    
RUN echo "memory_limit=4096M" > $PHP_INI_DIR/conf.d/memory_limit.ini
    
COPY . /var/www/html

#WORKDIR /var/www/html/symfony

#RUN composer install