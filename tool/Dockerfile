FROM php:7.4-cli-alpine

#RUN pecl install xdebug-2.8.1 \
#	&& docker-php-ext-enable xdebug



# RUN pecl install swoole-4.8.5 \
# 	pecl install redis-5.1.1 \
# 	&& docker-php-ext-enable swoole redis

RUN echo "https://mirrors.zju.edu.cn/alpine/edge/testing" >> /etc/apk/repositories

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.zju.edu.cn/g' /etc/apk/repositories


COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/
RUN install-php-extensions zip bz2 \
#    zstd lzf igbinary redis \
    swoole  \
    pdo_mysql mysqli
    #    mongodb \
    #    memcache memcached \
    #    mcrypt xlswriter imagick  \


RUN apk update

#RUN apk add php7-openssl libcrypto3 libressl3.5-libcrypto libssl3
RUN apk --no-cache add  \
#    php7-zip php7-bz2 libbz2 libzip\
    php7-brotli\
    php7-opcache \
#    php7-gd \
#    php7-pdo_mysql php7-mysqli libcrypto3 libressl3.5-libcrypto libssl3	openssl-dev\
#    php7-pecl-redis php7-pecl-zstd php7-pecl-igbinary php7-pecl-lzf zstd-libs \
#    php7-pecl-swoole libstdc++ curl-dev postgresql-dev linux-headers c-ares brotli-libs\
    php7-pecl-xlswriter \
    nodejs  \
    git  \
    composer

#COPY --from=composer/composer:latest-bin /composer /usr/bin/composer
RUN composer config -g repo.packagist composer "https://mirrors.aliyun.com/composer/"

#RUN php -m
#RUN php --ri opcache

WORKDIR /var/www/html/code
#RUN composer create-project swoft/swoft Swoft
#CMD  ["php","Swoft/bin/swoft","start"]
#COPY composer.phar /usr/bin
#RUN cp /usr/bin/composer.phar /usr/bin/composer \
#    && chmod +X /usr/bin/composer
##	&& composer
